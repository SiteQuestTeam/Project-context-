# Handoff: zmiana zadania na Smart City (3.10.2026, po południu)

Notatka dla nowej sesji. Cel nowej sesji: `/mattpocock-skills:grill-with-docs` na projekcie pod zadanie Smart City, potem nowy brief.

## Decyzja

**Zgłaszamy Sąsiedzisko do zadania SMART CITY (PKO), nie do HubMI.pl.** Zgłoszenie idzie tylko pod jedno zadanie.
Treść zadania, kryteria i regulamin: [zadanie-smart-city.md](zadanie-smart-city.md).

## Dlaczego nie HubMI.pl (ROPS)

Zespół był na stoisku ROPS. Wnioski:
- ROPS **nie chce oddolnych inicjatyw mieszkańców.** Kraków i Małopolska nie chcą oddolnych rozwiązań.
- ROPS chce platformy, która rozpowszechni **ich gotowe ~200 innowacji** wśród instytucji (NGO, gminy, szkoły, CUS) i pomoże tym instytucjom je wdrożyć oraz napisać wniosek („pomocnik w składaniu podań”).
- ROPS narzuca założenia i prosi, żeby nie dodawać za dużo funkcji. Nasze dodatki zasłoniłyby ich zadanie.
- Pasowanie wymagałoby odwrócenia kierunku produktu (instytucja → innowacja ROPS → plan wdrożenia). To nowy projekt.
- Prawa do kodu przechodzą na Proidea, a potem na Województwo.

## Dlaczego nie Kraków bez barier

- Zadanie dotyczy mapy dostępności miejsc i tras (schody, progi, windy) ze źródłem, datą i wiarygodnością każdej informacji. To inny produkt.
- Mentor (dyrektor IT) mówił o drugim problemie: miasto ręcznie sprawdza projekty modernizacji od deweloperów pod kątem wytycznych dostępności. Pomysł: platforma liczy, na ile procent projekt spełnia wytyczne. Za trudne na jedną noc (różne formaty plików projektowych).
- Nagroda 5 000 zł, prawa do kodu przechodzą na Gminę Kraków.

## Dlaczego Smart City pasuje

- Lista obszarów zadania ma wprost **„Communication between residents and public institutions”**. To rdzeń Sąsiedziska.
- Kryteria (Idea 30%, Relation 20%, Usability 20%, Design 20%, Completeness 10%) to te same, pod które pisaliśmy pierwszy brief.
- **Prawa autorskie zostają u nas.** Nagroda 8 000 zł.
- Wymagany tylko PDF (max 10 slajdów). Film, demo i repo są opcjonalne, ale pomagają.
- Ocena w 2 etapach: mentorzy czytają zgłoszenie, potem finaliści robią pitch.

## Co mówią mentorzy PKO

Chcą **rozwiązania konkretnego problemu społecznego**, nie ogólnej platformy. Można skupić się na jednej grupie.
Propozycja do grillowania: **samotność seniorów i to, że sąsiedzi się nie znają.** Ławki dla seniorów, spotkania pokoleń, kurs obsługi telefonu, park to przykłady w tej jednej historii.

## Pomysły użytkownika, które trzeba przegrillować

Pojawiły się w rozmowie, nie ma ich jeszcze w dokumentach:
1. **Ścieżka Potrzeby:** rozmowa mieszkańców przez określony czas (np. 7 dni) → opis projektu (Inicjatywa) → **głosowanie tak/nie**. Kłóci się z decyzją Q15 w [grilling-decisions.md](grilling-decisions.md) („głosowanie tylko w pitchu”) i z pojęciem Poparcia w [CONTEXT.md](../CONTEXT.md).
2. **Kraków to sandbox.** Docelowo każde miasto, mieszkaniec przypisany do społeczności przez **mObywatel**.
3. Nacisk na **wykluczenie cyfrowe** i poznawanie sąsiadów.
4. Pomysł asystenta: **dodawanie Potrzeby głosem** (senior mówi, AI pisze). Łączy wykluczenie cyfrowe z dostępnością.

## Rzeczy z analizy HubMI, które warto zachować

Nie są wymagane przez Smart City, ale podnoszą Usability i Design:
- Dostępność (WCAG 2.1 AA): kontrast, duży tekst, klawiatura, **lista obok mapy** (czytnik ekranu nie czyta Leaflet).
- Koszt utrzymania jako slajd (praktyczna użyteczność, gotowość do wdrożenia).

## Stan plików

- [BRIEF.md](../BRIEF.md) to teraz **wersja 2 pod HubMI. Jest nieaktualna.** Nie budować według niej.
- Wersja 1 briefu (bliższa Smart City) jest w git: `git show HEAD:BRIEF.md`.
- [docs/scope.md](scope.md), [CONTEXT.md](../CONTEXT.md), [docs/demo-scenario.md](demo-scenario.md), [docs/adr/0001](adr/0001-hubmi-task-not-krakow-task.md) mówią o HubMI. Do aktualizacji po grillu.
- ADR 0001 trzeba zastąpić nowym ADR („Smart City, nie HubMI”) z uzasadnieniem z tej notatki.
- Nic z tego nie jest zacommitowane.

## Do zrobienia po grillu

1. Nowy ADR o zmianie zadania.
2. Brief w wersji 3 pod Smart City.
3. Aktualizacja `scope.md`, `CONTEXT.md`, `demo-scenario.md`.
4. Pytania do mentora PKO: platforma zgłoszeń (Challenge Rocket czy Hack Tribe) i godzina końca (11:00 czy 23:00).
