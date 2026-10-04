# Mózg AI SideQuest

Dwa wywołania modelu AI (OpenAI `gpt-6.1-sol`). Każde ma swój prompt systemowy i schemat JSON odpowiedzi. Kod: repo [backend-ai](https://github.com/SiteQuestTeam/backend-ai). Słownik pojęć jest w [CONTEXT.md](../CONTEXT.md).

| Krok | Wejście | Prompt | Schemat |
|---|---|---|---|
| 1 | zdjęcie i dane | [prompt-1.md](prompt-1.md) | [schema-krok-1.json](schema-krok-1.json) |
| 2 | zdjęcie, typ, kategoria i odpowiedzi | [prompt-2.md](prompt-2.md) | [schema-krok-2.json](schema-krok-2.json) |

Teksty, które aplikacja pokazuje sama (nie AI), są w [stale-teksty.md](stale-teksty.md).

**Kopia robocza:** backend czyta prompty i schematy z [backend-ai/prompts/](https://github.com/SiteQuestTeam/backend-ai/tree/main/prompts). Testuj zmiany tam (`npm run czat`), a gotową wersję skopiuj tutaj, żeby oba miejsca były takie same.

## Przebieg

1. Gracz robi zdjęcie, opcjonalnie pisze linię „Co chcesz zgłosić?” i zaznacza „miejsce publiczne”.
2. **Krok 1.** Gdy pole `danger` nie jest puste, aplikacja pokazuje ostrzeżenie o możliwym zagrożeniu i pyta Gracza. Potwierdzenie kończy rozmowę, zaprzeczenie pozwala iść dalej. Gdy `status` nie jest `ok`, aplikacja pokazuje stały tekst. Przy `nowe_zdjecie` i `niezrozumiale` Gracz próbuje jeszcze raz, przy `opisz_zmiane` pisze linię. Potem znowu idzie krok 1.
3. Gdy jest `duplicate_of`, aplikacja pyta, czy to to samo. Tak = Zainteresowanie albo Głos, koniec.
4. Swipe typu albo `[ Dalej ]` (gdy `type_locked`).
5. Inicjatywa: Gracz odpowiada na 2 pytania. Usterka: bez pytań.
6. **Krok 2.** Przy `niezrozumiale` aplikacja pyta jeszcze raz. Przy `pytanie_zwrotne` Gracz odpowiada i krok 2 idzie jeszcze raz z `pytanie_zwrotne_juz_zadane: true`.
7. Inicjatywa: Gracz poprawia i zatwierdza Brief, serwer dopisuje miejsce i zdjęcie. Usterka: podgląd pól KCK z adresem i `[ Wyślij do KCK ]` ([docs/kck-integration.md](../docs/kck-integration.md)). Moduł KCK woła funkcję `przygotujUsterkeKck` z backend-ai.

## Dla programisty

- **Model:** OpenAI `gpt-6.1-sol` z `reasoning: {effort: "low"}`. Nazwa modelu w `.env` (`OPENAI_MODEL`), żeby dało się przejść na `gpt-6-astra` jedną linią, gdyby sol się mylił. Zdjęcie zmniejszone do 1024 px po dłuższym boku (nie `detail: low`, bo AI nie odczyta tablic). Szacunek: $0.03–0.06 za zgłoszenie. Klucz `OPENAI_API_KEY` tylko w `.env` backendu. Repo jest publiczne.
- **Wywołanie:** Responses API (`client.responses.create`). Prompt idzie w `instructions`. W `input` jest jedna wiadomość `user` z dwiema częściami: `{type: "input_image", image_url: "data:image/jpeg;base64,..."}` i `{type: "input_text", text: "<dane>...</dane>"}`. Pola bloku `<dane>` opisuje sekcja „Co dostajesz” w każdym prompcie.
- **Format odpowiedzi:** `text: {format: {type: "json_schema", name: "krok_1", schema: <plik>, strict: true}}`. Wynik jest w `response.output_text`.
- **Limity znaków:** tryb `strict` OpenAI nie obsługuje `minLength` i `maxLength`, więc ich nie ma w schematach. Sprawdź je na serwerze: tytuł (`title` Inicjatywy, `summary` Usterki) do 60 znaków; opis Usterki (`description`) do 500; problem Inicjatywy 60–250; pozostałe teksty Briefu do 250; `follow_up` i `who_fixes.reason` do 150; pytanie do 100; podpowiedź do 60. Gdy tekst jest za długi, utnij go albo poproś AI o krótszy. Prompty też podają te limity.
- **Odmowa:** gdy model odmówi, odpowiedź nie pasuje do schematu. Sprawdź to przed czytaniem JSON-a.
- **Kto naprawi:** Miasto, gdy `who_fixes.city_needed` jest `true`, inaczej Gracze. Liczy serwer.
- **Kategoria:** w kroku 1 serwer sprawdza, czy pasuje do typu (dwie listy są w opisie pola).
- **Zapis:** zapisz Brief od AI i Brief po poprawkach Gracza. Różnice posłużą do lepszych przykładów w promptach.
- **Punkty:** liczy tylko serwer. AI nigdy ich nie dostaje ani nie zwraca.
