# Automatyzacja Usterki z AI — KCK

> Wytyczne dla warstwy AI przygotowującej zgłoszenie Usterki do KCK.
>
> Pełna integracja KCK: [kck-integration.md](kck-integration.md).

## Cel

AI analizuje **Zdjęcie na żywo** i w jednym wywołaniu zwraca jeden z dwóch wyników:

- `OK` — na zdjęciu widać prawdziwą Usterkę; AI przygotowuje kategorię KCK, tytuł i opis,
- `RETAKE` — zdjęcie nie nadaje się do zgłoszenia; aplikacja prosi Gracza o nowe zdjęcie.

AI **nie wysyła zgłoszenia do KCK**. Przy `OK` wynik jest propozycją, którą Gracz widzi i może poprawić przed kliknięciem **„Wyślij do KCK”**.

## Flow

```text
Zdjęcie na żywo
      ↓
SideQuest Backend
      ↓
przygotujZdjecie()
      ↓
AI Vision — jedno wywołanie
      ↓
   ┌───────────────┐
   │               │
  OK            RETAKE
   │               │
   ↓               ↓
kategoria       powód +
tytuł           komunikat
opis               │
   │               ↓
   ↓           nowe zdjęcie
podgląd
   ↓
Gracz poprawia / akceptuje
   ↓
osobny flow wysyłki do KCK
```

## Wejście do AI

Moduł KCK przekazuje surowe zdjęcie:

```ts
przygotujUsterkeKck(photo: Buffer, {
  linia_gracza?: string,
  kategoria?: KategoriaKck | null,
})
```

Przed wysłaniem do modelu backend obraca zdjęcie zgodnie z EXIF, zmniejsza je maksymalnie do 1024 px po dłuższym boku i konwertuje do JPEG.

`linia_gracza` i wcześniejsza kategoria są tylko podpowiedzią. Usterka musi być widoczna na zdjęciu.

GPS i adres **nie są ustalane przez AI**. Obsługuje je osobno aplikacja / `AddressService`.

## Wynik AI

Publiczny wynik używany przez moduł KCK:

```ts
type KckAiResult =
  | {
      status: 'OK';
      category: 'DAMAGE' | 'POLLUTION' | 'GREENERY' | 'ANIMALS' | 'OTHER';
      summary: string;
      description: string;
    }
  | {
      status: 'RETAKE';
      reason:
        | 'NO_INCIDENT'
        | 'POOR_QUALITY'
        | 'FACES_OR_PLATES'
        | 'INAPPROPRIATE';
      message: string;
    };
```

### Przykład `OK`

```json
{
  "status": "OK",
  "category": "DAMAGE",
  "summary": "Uszkodzona nawierzchnia chodnika",
  "description": "Na chodniku widoczne jest uszkodzenie nawierzchni."
}
```

### Przykład `RETAKE`

```json
{
  "status": "RETAKE",
  "reason": "NO_INCIDENT",
  "message": "Nie widzę tu usterki. Zrób zdjęcie z bliska tego, co jest zepsute albo brudne."
}
```

Model wewnętrznie zwraca JSON zgodny z `prompts/schema-kck.json`. Schemat wymaga wszystkich pól; pola niepasujące do danego statusu mają wartość `null`. Backend następnie zamienia ten wynik na powyższy typ `KckAiResult`.

## Kategorie

AI może zwrócić tylko jedną z pięciu kategorii:

| Wartość | Znaczenie |
|---|---|
| `DAMAGE` | Uszkodzenia |
| `POLLUTION` | Zanieczyszczenia i odory |
| `GREENERY` | Zieleń |
| `ANIMALS` | Zwierzęta |
| `OTHER` | Pozostałe |

`OTHER` oznacza **prawdziwą Usterkę**, która nie pasuje do czterech pozostałych kategorii.

`OTHER` **nie jest fallbackiem dla niejasnego zdjęcia**. Jeżeli nie da się potwierdzić Usterki na zdjęciu, wynik powinien być `RETAKE`.

Mapowanie kategorii na `serviceExternalId` wykonuje backend KCK, nie model AI.

## RETAKE

Dozwolone powody:

| Powód | Kiedy |
|---|---|
| `NO_INCIDENT` | Na zdjęciu nie widać Usterki miejskiej |
| `POOR_QUALITY` | Zdjęcie jest zbyt słabe, aby wiarygodnie rozpoznać problem |
| `FACES_OR_PLATES` | Głównym elementem jest twarz / duża twarz albo czytelna tablica rejestracyjna |
| `INAPPROPRIATE` | Treść jest obraźliwa albo nieprzyzwoita |

Przy `RETAKE` AI zwraca krótki komunikat mówiący Graczowi, jak poprawić zdjęcie. Nie generuje wtedy kategorii, tytułu ani opisu zgłoszenia.

## Reguły promptu

Źródłem promptu jest:

```text
prompts/prompt-kck.md
```

Najważniejsze reguły:

- Usterka musi być rzeczywiście widoczna na zdjęciu.
- AI nie wymyśla adresu, ulicy, przyczyny, czasu powstania, właściciela terenu ani odpowiedzialnego urzędu.
- `kategoria_podpowiedz` jest tylko sugestią; zdjęcie ma pierwszeństwo.
- `summary` opisuje problem, nie lokalizację.
- `description` opisuje wyłącznie to, co można wiarygodnie wywnioskować ze zdjęcia.
- AI pisze po polsku, krótko i rzeczowo.
- Wynik musi być zgodny ze ścisłym JSON Schema.

## Walidacja backendu

Backend wykonuje twardą walidację wyniku.

Dla `OK`:

```text
category    = jedna z 5 kategorii KCK
summary     = 1–60 znaków
description = 1–500 znaków
```

Jeżeli model złamie te reguły, wynik jest odrzucany jako błąd AI (`AiBlad`).

Dla `RETAKE` wymagane są:

```text
retake_reason
message
```

Brak któregoś z nich również oznacza błąd AI.

## Integracja z backendem

Funkcja przeznaczona dla modułu KCK:

```ts
przygotujUsterkeKck(photo)
```

Docelowy flow `POST /kck/prepare`:

```text
photo ───────→ przygotujUsterkeKck() ─→ OK / RETAKE
latitude/lng → AddressService ─────────→ street + number + zipCode
```

Przy `OK` backend łączy wynik AI z adresem wyliczonym z GPS i zwraca podgląd zgłoszenia.

Przy `RETAKE` nie przygotowuje zgłoszenia do wysłania — aplikacja prosi o nowe zdjęcie.

## Błąd AI i fallback

`RETAKE` **nie jest awarią AI**. Jest poprawnym wynikiem analizy zdjęcia.

Fallback do ręcznych pól stosujemy dopiero, gdy AI faktycznie zawiedzie, np.:

- timeout,
- odmowa modelu,
- niepełna odpowiedź,
- niepoprawny JSON,
- wynik niezgodny ze schematem,
- złamanie twardych limitów.

Wtedy Usterka nadal może zostać zgłoszona ręcznie:

```text
Kategoria: [ wybierz ]
Tytuł:     [ ... ]
Opis:      [ ... ]
```

Awaria AI **nie może blokować wysłania Usterki do KCK**.

## Parametry wywołania AI

Aktualna implementacja:

- jedno wywołanie modelu dla Usterki,
- Structured Output przez `json_schema`,
- `strict: true`,
- `store: false`,
- domyślny timeout: **8 s**,
- `maxRetries: 0`.

Brak automatycznych ponowień utrzymuje przewidywalny czas odpowiedzi. Decyzja o ponowieniu należy do aplikacji.

## Ważne zasady

- AI przygotowuje propozycję, nie podejmuje ostatecznej decyzji za Gracza.
- AI nie wysyła requestu do KCK.
- AI nie nalicza Punktów.
- AI nie określa adresu.
- AI nie wybiera wydziału ani urzędu.
- `OTHER` nie zastępuje `RETAKE`.
- `RETAKE` nie jest błędem technicznym.
- Klucz API modelu znajduje się wyłącznie na backendzie.
- Ostateczne dane `OK` zatwierdza Gracz przed wysłaniem.
