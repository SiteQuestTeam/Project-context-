# Integracja SideQuest z Krakowskim Centrum Kontaktu (KCK)

> Status: obowiązujące wytyczne dla ścieżki zgłaszania **usterek miejskich** w MVP.
>
> Usterka jest osobną ścieżką od Inicjatywy. Inicjatywy nadal działają według `MVP.md`; typowe usterki miejskie są przekazywane wyłącznie do KCK.

## Cel

Zastąpić czterokrokowy formularz KCK prostym flow w SideQuest:

```text
Zdjęcie na żywo
      ↓
GPS
      ↓
AI: kategoria + tytuł + opis
      ↓
GPS → adres
      ↓
Podgląd i edycja przez Gracza
      ↓
[ Wyślij do KCK ]
      ↓
SideQuest Backend
      ↓
KCK
      ↓
incidentId
```

Gracz nie wybiera wydziału ani jednostki miejskiej. SideQuest przygotowuje dane, ale **ostatnie wysłanie zawsze wymaga świadomego kliknięcia przez Gracza**.

## Zasady UX

1. Zdjęcie jest robione aparatem w aplikacji; bez galerii.
2. GPS pobierany jest automatycznie.
3. AI proponuje:
   - kategorię KCK,
   - tytuł,
   - krótki opis.
4. Adres jest wyznaczany automatycznie z GPS.
5. Gracz widzi pełny podgląd i może poprawić kategorię, tytuł, opis lub adres.
6. Dopiero kliknięcie **„Wyślij do KCK”** powoduje prawdziwe zgłoszenie.
7. W MVP zgłoszenie do KCK jest anonimowe — bez imienia, nazwiska, e-maila i telefonu.
8. Sukces pokazujemy dopiero po otrzymaniu `incidentId` z KCK.

Nie robimy dla usterki:
- pytań „Kto naprawi”,
- wyboru urzędu lub wydziału,
- Głosów i Progu,
- konta KCK,
- wyboru kanału powiadomień.

## Kategorie KCK

AI klasyfikuje zdjęcie tylko do jednej z pięciu klas:

| SideQuest | KCK | `serviceExternalId` |
|---|---|---|
| `DAMAGE` | Uszkodzenia | `30492-uszkodzenia` |
| `POLLUTION` | Zanieczyszczenia i odory | `64665-zanieczyszczenia` |
| `GREENERY` | Zieleń | `51517-zielen` |
| `ANIMALS` | Zwierzęta | `09150-zwierzeta` |
| `OTHER` | Pozostałe | `40583-pozostale` |

Przykład:

```ts
export const KCK_CATEGORY_IDS = {
  DAMAGE: '30492-uszkodzenia',
  POLLUTION: '64665-zanieczyszczenia',
  GREENERY: '51517-zielen',
  ANIMALS: '09150-zwierzeta',
  OTHER: '40583-pozostale',
} as const;

export type KckCategory = keyof typeof KCK_CATEGORY_IDS;
```

Na hackathon wartości mogą być zahardcodowane. KCK sam pobiera kategorie dynamicznie, więc integrację należy trzymać za osobną warstwą, aby później łatwo odświeżyć mapowanie.

## Endpoint KCK

Frontend KCK wysyła zgłoszenie jednym requestem:

```http
POST https://kontakt.krakow.pl/api/e-incident/1.0.0/incident/create
Content-Type: multipart/form-data; boundary=...
```

Nie automatyzujemy przeglądarki, nie używamy Playwrighta/Selenium i nie odtwarzamy czterech ekranów KCK.

### Body

Request jest `multipart/form-data` i zawiera:

- `dto` — JSON zapisany jako string,
- `file` — zdjęcie; przy wielu zdjęciach pole `file` jest dodawane wielokrotnie.

Schemat:

```text
dto  = "{...JSON...}"
file = photo.jpg
file = photo2.jpg
```

Nie ustawiamy ręcznie nagłówka `Content-Type`; klient HTTP musi sam wygenerować poprawny `boundary`.

## DTO wysyłane do KCK

Dla anonimowej usterki:

```ts
interface KckIncidentDto {
  requestType: 'ISSUE';

  summary: string;
  description: string;

  streetName: string;
  buildingNumber: string;
  zipCode: string;

  latitude: number;
  longitude: number;

  layer: 'Standardowa';
  object: '';

  userFirstName: '';
  userLastName: '';
  userEmail: '';
  userPhoneNumber: '';

  processingOfPersonalAgreement: false;
  emailNotificationAgreement: false;
  smsNotificationAgreement: false;

  serviceExternalId: string;
}
```

Przykład:

```json
{
  "requestType": "ISSUE",
  "summary": "Uszkodzona nawierzchnia chodnika",
  "description": "Na chodniku znajduje się uszkodzona nawierzchnia utrudniająca przejście.",
  "streetName": "Stanisława Lema",
  "buildingNumber": "7",
  "zipCode": "31-571",
  "latitude": 50.0644,
  "longitude": 19.9438,
  "layer": "Standardowa",
  "object": "",
  "userFirstName": "",
  "userLastName": "",
  "userEmail": "",
  "userPhoneNumber": "",
  "processingOfPersonalAgreement": false,
  "emailNotificationAgreement": false,
  "smsNotificationAgreement": false,
  "serviceExternalId": "30492-uszkodzenia"
}
```

## Zdjęcia

Kod frontendu KCK:
- używa pola `file`,
- obsługuje wiele plików przez wielokrotne `append("file", ...)`,
- domyślnie ogranicza liczbę zdjęć do 5,
- domyślnie ogranicza rozmiar pojedynczego pliku do 7 MiB,
- przyjmuje obrazy.

W SideQuest MVP wymagamy jednego Zdjęcia na żywo. Przed wysłaniem warto skompresować zdjęcie do rozsądnego rozmiaru, ale nie zmieniać go tak, aby utraciło użyteczność dowodową.

## Odpowiedź KCK

Po sukcesie frontend KCK wyświetla:

```ts
response.data.incidentId
```

SideQuest uznaje wysłanie za zakończone wyłącznie wtedy, gdy otrzyma prawidłowy `incidentId`.

Przykład odpowiedzi SideQuest:

```json
{
  "status": "SUBMITTED",
  "incidentId": "888218"
}
```

UI:

```text
✓ Zgłoszenie przekazane do KCK
Numer zgłoszenia: 888218
```

## Autoryzacja

Dla anonimowego zgłoszenia frontend KCK nie dodaje tokena Bearer.

Nagłówek:

```http
Authorization: Bearer ...
```

jest dodawany tylko dla zalogowanego użytkownika KCK, gdy wykorzystywane są jego dane.

W MVP SideQuest wysyła usterki anonimowo, więc nie potrzebuje logowania do KCK.

## GPS → adres

KCK korzysta z miejskiej usługi adresowej:

```text
https://msip.um.krakow.pl/arcgis/rest/services/adresy_search/MapServer/0
```

Dla pozycji GPS wyszukuje adres w pobliżu i mapuje:

```text
kod_kod → zipCode
ulica   → streetName
adr_nr  → buildingNumber
```

KCK używa wyszukiwania w promieniu do 400 m i wybiera najbliższy wynik. Gdy brak wyniku, używa reverse geocodingu ArcGIS.

W SideQuest logika adresowa powinna być po stronie backendu lub w osobnym serwisie `AddressService`. Jeśli adresu nie da się ustalić jednoznacznie, Gracz musi go poprawić przed wysłaniem.

## API SideQuest

Wystarczą dwa endpointy.

### `POST /kck/prepare`

Wejście:

```text
multipart/form-data

photo
latitude
longitude
```

Backend równolegle:
- wysyła zdjęcie do AI,
- zamienia GPS na adres.

Odpowiedź:

```json
{
  "category": "DAMAGE",
  "serviceExternalId": "30492-uszkodzenia",
  "summary": "Uszkodzona nawierzchnia chodnika",
  "description": "Na chodniku znajduje się uszkodzona nawierzchnia.",
  "address": {
    "streetName": "Stanisława Lema",
    "buildingNumber": "7",
    "zipCode": "31-571"
  },
  "latitude": 50.0644,
  "longitude": 19.9438
}
```

To jest tylko propozycja — nic nie jest jeszcze wysłane do KCK.

### `POST /kck/submit`

Wywoływany dopiero po potwierdzeniu przez Gracza.

Wejście:
- zdjęcie,
- kategoria,
- tytuł,
- opis,
- adres,
- GPS.

Backend:
1. waliduje dane,
2. mapuje kategorię na `serviceExternalId`,
3. buduje `KckIncidentDto`,
4. tworzy `FormData`,
5. dodaje `dto`,
6. dodaje `file`,
7. wykonuje POST do KCK,
8. zwraca `incidentId`.

## NestJS — podział odpowiedzialności

```text
src/
  kck/
    kck.module.ts
    kck.controller.ts
    kck.service.ts
    kck.client.ts
    kck.constants.ts
    dto/
      prepare-kck.dto.ts
      submit-kck.dto.ts
  address/
    address.service.ts
```

- `KckController` — endpointy SideQuest.
- `KckService` — orkiestracja prepare/submit.
- `KckClient` — wyłącznie komunikacja z zewnętrznym API KCK.
- `AddressService` — GPS → adres.
- moduł AI — klasyfikacja, tytuł i opis.

KCK jest zewnętrzną, nieudokumentowaną integracją, dlatego szczegóły endpointu nie mogą być rozsiane po aplikacji.

## Szkic KckClient

```ts
async submitIncident(
  input: SubmitKckIncidentDto,
  photo: Express.Multer.File,
) {
  const dto: KckIncidentDto = {
    requestType: 'ISSUE',
    summary: input.summary,
    description: input.description,

    streetName: input.streetName,
    buildingNumber: input.buildingNumber,
    zipCode: input.zipCode,

    latitude: input.latitude,
    longitude: input.longitude,

    layer: 'Standardowa',
    object: '',

    userFirstName: '',
    userLastName: '',
    userEmail: '',
    userPhoneNumber: '',

    processingOfPersonalAgreement: false,
    emailNotificationAgreement: false,
    smsNotificationAgreement: false,

    serviceExternalId: KCK_CATEGORY_IDS[input.category],
  };

  const form = new FormData();
  form.append('dto', JSON.stringify(dto));
  form.append(
    'file',
    new Blob([photo.buffer], { type: photo.mimetype }),
    photo.originalname,
  );

  const response = await fetch(
    'https://kontakt.krakow.pl/api/e-incident/1.0.0/incident/create',
    {
      method: 'POST',
      body: form,
    },
  );

  if (!response.ok) {
    throw new Error(`KCK returned HTTP ${response.status}`);
  }

  const result = await response.json();

  if (!result?.incidentId) {
    throw new Error('KCK response does not contain incidentId');
  }

  return {
    incidentId: String(result.incidentId),
  };
}
```

## Dane po stronie SideQuest

Minimalny zapis:

```ts
CityIncident {
  id
  playerId

  latitude
  longitude

  category
  summary
  description

  photoUrl

  kckIncidentId
  status

  createdAt
  updatedAt
}
```

Statusy:

```ts
PREPARED
SUBMITTING
SUBMITTED
FAILED
```

KCK jest źródłem prawdy o dalszej obsłudze sprawy. SideQuest przechowuje przede wszystkim fakt przygotowania/wysłania i numer KCK.

## Ochrona przed podwójnym wysłaniem

Po kliknięciu „Wyślij do KCK” przycisk jest blokowany do czasu odpowiedzi.

Backend powinien przyjmować `submissionId` / klucz idempotencyjny, aby ponowienie tego samego requestu z powodu timeoutu lub podwójnego kliknięcia nie tworzyło świadomie drugiego zgłoszenia po stronie SideQuest.

Ponieważ KCK nie udostępnia nam udokumentowanego mechanizmu idempotencyjnego, po niejednoznacznym timeoutcie nie należy automatycznie ponawiać POST bez kontroli.

## Obsługa błędów

### AI nie działa

Nie blokujemy zgłoszenia. Pokazujemy ręczne pola:

```text
Kategoria: [...]
Tytuł: [...]
Opis: [...]
```

### Nie udało się ustalić adresu

Gracz poprawia adres przed wysłaniem.

### KCK zwraca błąd

Nie pokazujemy sukcesu i nie przyznajemy statusu `SUBMITTED`.

UI:

```text
Nie udało się przekazać zgłoszenia do KCK.
Zgłoszenie nie zostało wysłane.

[ Spróbuj ponownie ]
```

### Timeout

Traktujemy jako wynik niejednoznaczny. Nie wykonujemy automatycznie kolejnego POST, jeśli nie wiemy, czy KCK przyjęło pierwszy.

## Granica odpowiedzialności

```text
SideQuest App
      │
      │ zdjęcie + GPS
      ▼
SideQuest Backend
      ├── AI
      ├── AddressService
      └── KckClient
              │
              ▼
             KCK
              │
              ▼
          incidentId
```

Aplikacja mobilna **nie komunikuje się bezpośrednio z API KCK**.

## MVP — Definition of Done

Integracja usterki z KCK jest gotowa, gdy:

- [ ] zdjęcie jest robione z aparatu SideQuest,
- [ ] GPS jest pobierany automatycznie,
- [ ] AI zwraca jedną z 5 kategorii, tytuł i opis,
- [ ] GPS jest zamieniany na adres,
- [ ] Gracz może sprawdzić i poprawić dane,
- [ ] prawdziwy POST do KCK następuje dopiero po kliknięciu „Wyślij do KCK”,
- [ ] zgłoszenie jest anonimowe,
- [ ] zdjęcie trafia jako pole `file`,
- [ ] DTO trafia jako pole `dto`,
- [ ] sukces wymaga `incidentId`,
- [ ] `incidentId` jest zapisany i pokazany Graczowi,
- [ ] błędy AI, geocodingu i KCK mają bezpieczny fallback,
- [ ] aplikacja nie tworzy celowo duplikatów.

## Ważne ograniczenie

Endpoint KCK został ustalony na podstawie aktualnego frontendu KCK i nie jest publicznym, wersjonowanym kontraktem SideQuest. Może się zmienić. Dlatego integracja musi być zamknięta w `KckClient`, a przed demo należy wykonać kontrolny test poprawnego zgłoszenia.
