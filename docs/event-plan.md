# Plan na hackathonie: co robimy po kolei

Bez godzin, tylko kolejność. Termin: niedziela 4 października, przyjmujemy 11:00 rano (do potwierdzenia u mentora PKO).
Pojęcia: [CONTEXT.md](../CONTEXT.md). Zakres: [scope.md](scope.md).

## Jak to jest zbudowane

- **Aplikacja (Patryk):** `SiteQuestTeam/App`. Mapa, aparat, GPS, skaner kodu QR. Musi się otwierać z linku (jury).
- **Serwer (Szymon):** `SiteQuestTeam/Backend`. **Wszystkie Punkty przyznaje serwer, nigdy telefon.** Serwer sprawdza odległość od Hubu, ważność kodu Rajdu i dzienny limit.
- **Baza (Gabriel):** wybiera zespół techniczny ([ADR 0009](adr/0009-tech-team-owns-the-stack.md)). Potrzebne: mapy (odległości), logowanie, zdjęcia.
- **Kod Rajdu** zmienia się co 30 sekund (podpisany przez serwer), więc zrzut ekranu wysłany do domu nie działa.
- **Księga Punktów:** każdy Punkt to jeden wiersz z powodem. Liga dzielnic to jedno zapytanie: godziny w dzielnicy ÷ mieszkańcy × 1000, w bieżącym miesiącu.
- **Hosting:** serwer nie może „usypiać” (darmowe hostingi budzą się ok. 50 s, to zabija demo na żywo). Wybiera Gabriel.

## Zespół techniczny

1. **Wszyscy trzej:** publiczne repozytorium (`.env` w `.gitignore`), baza, pusta aplikacja i serwer w internecie. Dalej dopiero, gdy „hello” działa na prawdziwym telefonie.
2. **Gabriel:** tabele + dane przykładowe: 18 dzielnic z prawdziwą liczbą mieszkańców, ok. 20 Hubów, lista Misji od zespołu psychologicznego, ok. 50 przykładowych Graczy.
3. **Szymon:** endpointy w kolejności historii Oli: Dowód Misji → Rajd (załóż / dołącz / Odbicie / zamknij) → Punkty i Rangi → Weryfikacja → Liga → Widok dla miasta.
4. **Patryk:** ekrany w tej samej kolejności. Najpierw brzydkie, potem ładne.
5. **Pierwszy pełny przebieg historii Oli** od początku do końca. Dopiero potem wygląd (Design to 20%).
6. **Poziom 2**, tylko jeśli Poziom 1 działa.
7. **Koniec nowych funkcji** kilka godzin przed terminem. Potem tylko poprawki.

## Zespół psychologiczny (równolegle)

1. Zasady gry: ile Punktów za co, progi Rang, lista Odznak, próg Weryfikatora. **Daje je Gabrielowi jak najwcześniej.**
2. Lista ok. 15 Misji i tematy Sezonów.
3. 3 wymyśleni Sponsorzy i ich Nagrody.
4. Nazwy: znajomi, słowa w grze (aplikacja to SideQuest).
5. PDF max 10 slajdów (musi się bronić bez nas), pitch, slajd z kosztem utrzymania i modelem biznesowym.
6. Test z prawdziwymi ludźmi na hali: czy rozumieją grę w 30 sekund?
7. Pytania do mentora PKO: platforma zgłoszeń i godzina końca.

## Na koniec (wszyscy)

1. README z sekcją „Użycie AI”.
2. Zapasowy film z demo (gdyby internet na hali padł).
3. Próba pitchu z demo na telefonie, z prawdziwym skanem kodu.
4. Wysyłamy z zapasem, nie w ostatniej minucie.
