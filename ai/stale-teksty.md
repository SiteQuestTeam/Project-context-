# Stałe teksty w aplikacji

Te teksty pokazuje aplikacja, a nie AI. AI ich nie pisze, więc nie może w nich niczego wymyślić. Każde słowo zatwierdza Tomasz. Wszystkie teksty mają formy neutralne płciowo: tryb rozkazujący i czas teraźniejszy, bez „zrobiłeś” i „mógłbyś”.

Linie nauki (oznaczone 💡) aplikacja pokazuje w pierwszych 3 zgłoszeniach Gracza. Potem zwija je i można je rozwinąć.

## Ekran 1: aparat

- Pole pod zdjęciem: **„Co chcesz zgłosić?”** (opcjonalnie)

## Możliwe zagrożenie (pole `danger` z kroku 1)

Gdy `danger` nie jest `null`, aplikacja pokazuje ostrzeżenie i pyta Gracza. AI może się pomylić, więc rozmowę przerywa dopiero potwierdzenie Gracza.

- **„⚠️ AI widzi możliwe zagrożenie: {danger}”**
- „Czy to naprawdę się dzieje?” `[ Tak, widzę to ]` `[ Nie, nic takiego tu nie ma ]`
- Tak: „Odejdź od tego miejsca i zadzwoń pod 112. Tego nie zgłaszamy w SideQuest, bo tu potrzebne są służby ratunkowe.” **Rozmowa się kończy**, zgłoszenia nie ma.
- Nie: „Dzięki. Idziemy dalej.” Rozmowa idzie dalej normalnie.

## Przechodnie na zdjęciu (pole `faces_in_background` z kroku 1)

Gdy `true`, zdjęcie przechodzi, a aplikacja pokazuje informację:

- „👤 Na zdjęciu widać przechodniów. Są tylko szczegółem ulicy, więc zdjęcie może trafić na mapę. Prawo autorskie (art. 81 ust. 2 pkt 2) pozwala pokazać osobę, która jest tylko szczegółem większej całości, na przykład zgromadzenia albo krajobrazu.”

W pełnej wersji (pitch): automatyczne rozmywanie twarzy.

## Odpowiedzi na `status` z kroku 1

| status | Tekst |
|---|---|
| `nowe_zdjecie` | `message` od AI i przycisk `[ Zrób nowe zdjęcie ]` |
| `nie_widac_usterki` | `message` od AI i przyciski `[ Zrób nowe zdjęcie ]` `[ Popraw opis ]` |
| `opisz_zmiane` | „Nie widzę tu usterki. Napisz, co chcesz zmienić w tym miejscu.” Bez podpowiedzi. |
| `niezrozumiale` | „Nie rozumiem tej odpowiedzi. Napisz ją jeszcze raz, innymi słowami.” |

## Teren publiczny

Przy każdym zgłoszeniu Gracz zaznacza pole:
- ☐ „To miejsce jest publiczne: ulica, chodnik, park, plac albo podwórko osiedla.”

## Duplikat (`duplicate_of`)

- Pytanie: „To chyba to samo co „{tytuł}”. Chodzi o to samo?” `[ Tak ]` `[ Nie, to co innego ]`
- Tak, Usterka: „Dzięki. Twoje Zainteresowanie jest zapisane. +{n} Punktów. Znajdziesz to w Historii.”
- Tak, Inicjatywa zbiera głosy: „Ta Inicjatywa już jest na mapie. Poprzyj ją Głosem.” `[ Oddaj Głos ]`
- Tak, Inicjatywa przeszła: „Ta Inicjatywa już przeszła. +{n} Punktów za Zainteresowanie.”

## Swipe typu

- `type_locked: false`: `type_reason` od AI i `← Usterka | Inicjatywa →`
- `type_locked: true`: `type_reason` od AI i przycisk `[ Dalej ]`. Nie ma swipe'a.

## 💡 „Dlaczego pytam” (Inicjatywa)

| topic | Tekst |
|---|---|
| `dzialanie` | „Budżet Obywatelski prosi o szczegółowy opis. Konkret, na przykład „stojak na 6 rowerów”, ma większą szansę niż ogólnik.” |
| `zasoby` | „W inicjatywie lokalnej miasto pyta, ile pracy dadzą sami mieszkańcy. Za tę pracę wniosek dostaje punkty.” |

Źródła: [research 1a i 1b](../docs/research-ai-form.md).

## Odpowiedzi na `status` z kroku 2

| status | Tekst |
|---|---|
| `niezrozumiale` | Ten sam tekst co w kroku 1, potem to samo pytanie jeszcze raz. |
| `pytanie_zwrotne` | `follow_up` od AI i pole odpowiedzi |

## Brief Inicjatywy i zgłoszenie Usterki

- Tekst z `source: "ai"` dostaje znacznik: „✨ propozycja AI. Popraw ją, jeśli wiesz lepiej.”
- Inicjatywa: „Sprawdź swój Brief.” `[ Popraw ]` `[ Opublikuj ]`
- Usterka (podgląd zgłoszenia do KCK, [docs/kck-integration.md](../docs/kck-integration.md)): „Sprawdź, czy dane są poprawne.” Pola: kategoria KCK, tytuł, opis, adres. `[ Popraw ]` `[ Wyślij do KCK ]`
- Nazwy kategorii KCK: `DAMAGE` Uszkodzenia, `POLLUTION` Zanieczyszczenia i odory, `GREENERY` Zieleń, `ANIMALS` Zwierzęta, `OTHER` Pozostałe.

## Po wysłaniu: Usterka

Pokazujemy dopiero po otrzymaniu `incidentId` z KCK.

- „✓ Zgłoszenie przekazane do KCK. Numer zgłoszenia: {incidentId}.”
- 💡 „Po tym numerze sprawdzisz na kontakt.krakow.pl, co dzieje się ze sprawą. Ponad 80% zgłoszeń kończy się interwencją miasta.”
- 💡 „Jedna dziura to Usterka. Ale jeśli cała ulica wymaga zmiany, na przykład nowego chodnika albo progu zwalniającego, możesz zgłosić Inicjatywę.”

Źródło liczby: [research 1c](../docs/research-ai-form.md) (84% w styczniu–sierpniu 2026) i [krakow.pl](https://krakow.pl/aktualnosci/338837,29,komunikat,masz_problem_w_krakowie__83_proc__zgloszen_do_kck_konczy_sie_skuteczna_interwencja.html) (83%).

## 🏛️ „Co dalej w mieście” (Inicjatywa)

Wybiera reguła w kodzie, a nie AI: Kto naprawi = Miasto, gdy `city_needed: true`.

**Przy publikacji (krótko):**
- Miasto: „Twój Brief ma format Budżetu Obywatelskiego. Gdy zbierze {Próg} Głosów, pokażemy, jak złożyć go w mieście.”
- Gracze: „Tę zmianę możecie zrobić sami z sąsiadami. Gdy zbierze {Próg} Głosów, pokażemy, jak zacząć.”

**Przy „Przeszła” (całość), szkic do sprawdzenia:**
- Miasto:
  - „**Budżet Obywatelski:** złóż projekt na budzet.krakow.pl. Potrzebujesz 15 podpisów mieszkańców. Tytuł i kategoria z Briefu pasują do formularza.”
  - „**Inicjatywa lokalna:** zrób to razem z miastem. Wy dajecie pracę, miasto pomaga. Realizacja zaczyna się najwcześniej 8 tygodni po złożeniu wniosku. Gdy teren nie należy do miasta, potrzebna jest zgoda właściciela.”
- Gracze:
  - „**Zróbcie to sami:** umówcie się z osobami, które oddały Głos.”
  - „Gdy potrzebne są pieniądze albo sprzęt, złóż wniosek o inicjatywę lokalną. Miasto może pomóc.”

Źródła: [research 1a (inicjatywa lokalna) i 1b (Budżet Obywatelski)](../docs/research-ai-form.md).
