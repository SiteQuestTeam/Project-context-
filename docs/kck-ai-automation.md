# Automatyzacja Usterki z AI — KCK

> Małe wytyczne tylko dla warstwy AI przygotowującej zgłoszenie Usterki do KCK.
>
> Pełna integracja KCK: [kck-integration.md](kck-integration.md).

## Cel

AI ma maksymalnie uprościć zgłoszenie Usterki. Gracz robi **Zdjęcie na żywo**, a backend automatycznie przygotowuje trzy pola:

1. kategorię KCK,
2. tytuł,
3. krótki opis.

AI **nie wysyła zgłoszenia do KCK**. Wynik jest tylko propozycją, którą Gracz widzi i może poprawić przed kliknięciem **„Wyślij do KCK”**.

## Flow

```text
Zdjęcie na żywo
      ↓
SideQuest Backend
      ↓
AI Vision
      ↓
kategoria + tytuł + opis
      ↓
walidacja JSON
      ↓
podgląd dla Gracza
      ↓
Gracz poprawia / akceptuje
      ↓
osobny flow wysyłki do KCK
```

## Wejście do AI

Minimalne wejście:

```ts
{
  photo: Buffer
}
```

GPS i adres **nie powinny być wymyślane przez AI**. Są pobierane osobno przez aplikację i `AddressService`.

## Oczekiwany wynik

AI musi zwracać wyłącznie JSON zgodny ze schematem:

```ts
type KckAiResult = {
  category:
    | 'DAMAGE'
    | 'POLLUTION'
    | 'GREENERY'
    | 'ANIMALS'
    | 'OTHER';

  summary: string;
  description: string;
};
```

Przykład:

```json
{
  "category": "DAMAGE",
  "summary": "Uszkodzona nawierzchnia chodnika",
  "description": "Na chodniku widoczne jest uszkodzenie nawierzchni, które może utrudniać bezpieczne przejście."
}
```

## Kategorie

AI może wybrać tylko jedną z pięciu kategorii:

| Wartość | Znaczenie |
|---|---|
| `DAMAGE` | Uszkodzenia |
| `POLLUTION` | Zanieczyszczenia i odory |
| `GREENERY` | Zieleń |
| `ANIMALS` | Zwierzęta |
| `OTHER` | Pozostałe |

Mapowanie na `serviceExternalId` wykonuje backend, nie model AI.

## Reguły promptu

Model powinien dostać prostą instrukcję:

```text
Analizujesz zdjęcie usterki miejskiej z Krakowa.

Na podstawie wyłącznie tego, co rzeczywiście widać na zdjęciu:
1. wybierz jedną kategorię:
   DAMAGE, POLLUTION, GREENERY, ANIMALS, OTHER
2. utwórz krótki tytuł,
3. utwórz krótki, rzeczowy opis.

Nie wymyślaj:
- adresu,
- przyczyny problemu,
- czasu powstania,
- właściciela terenu,
- odpowiedzialnego urzędu,
- informacji, których nie można wywnioskować ze zdjęcia.

Jeżeli zdjęcie jest niejednoznaczne, wybierz OTHER i opisz tylko to, co widać.

Zwróć wyłącznie JSON zgodny ze schematem.
```

## Walidacja po stronie backendu

Backend musi sprawdzić wynik AI przed pokazaniem go w aplikacji:

- `category` należy do 5 dozwolonych wartości,
- `summary` nie jest pusty,
- `description` nie jest pusty,
- odpowiedź jest poprawnym JSON-em,
- brak dodatkowych, nieoczekiwanych pól nie blokuje działania, ale nie są one używane.

Rekomendowane limity:

```text
summary     <= 60 znaków
description <= 500 znaków
```

## Integracja z backendem

AI jest wywoływane w:

```http
POST /kck/prepare
```

Endpoint wykonuje równolegle:

```text
photo ───────→ AI ─────────→ category + summary + description
latitude/lng → AddressService → street + number + zipCode
```

Dopiero backend łączy oba wyniki w gotowy podgląd.

## Fallback

Jeżeli AI:
- nie odpowie,
- przekroczy timeout,
- zwróci błędny JSON,
- zwróci kategorię spoza listy,

to zgłoszenie nadal ma być możliwe.

Frontend pokazuje wtedy ręczne pola:

```text
Kategoria: [ wybierz ]
Tytuł:     [ ... ]
Opis:      [ ... ]
```

Awaria AI **nie może blokować wysłania Usterki do KCK**.

## Ważne zasady

- AI przygotowuje propozycję, nie podejmuje ostatecznej decyzji za Gracza.
- AI nie wysyła requestu do KCK.
- AI nie nalicza Punktów.
- AI nie określa adresu.
- AI nie wybiera wydziału ani urzędu.
- Klucz API modelu znajduje się wyłącznie na backendzie w `.env`.
- Ostateczne dane zatwierdza Gracz przed wysłaniem.
