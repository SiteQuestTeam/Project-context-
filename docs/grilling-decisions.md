# Dziennik decyzji z grillowania (30 września 2026)

Krótki zapis każdej decyzji z sesji `grill-with-docs`, żeby nowa sesja (albo nowa osoba) nie musiała czytać rozmowy.
Pojęcia: [CONTEXT.md](../CONTEXT.md). Większe decyzje z uzasadnieniem: [adr/](adr/).
Numery Q są z sesji; brak Q10 w kolejności, bo zostało przesunięte do rundy 3.

## Zadanie i forma

- **Zadanie:** HubMI.pl (15 000 PLN), nie „Cracow without barriers”. → [ADR 0001](adr/0001-hubmi-task-not-krakow-task.md)
- **Q1 Historia dla jury:** mieszkaniec najpierw (scenariusz z ławkami), mapa dla Urzędnika jako ostatni ekran. → [demo-scenario.md](demo-scenario.md)
- **Q5 Język:** aplikacja i pitch po polsku, kod i repozytorium po angielsku.
- **Q6 Forma:** jedna PWA (strona + ikona na telefonie). → [ADR 0002](adr/0002-pwa-not-native-app.md)
- **Q12/Q18 Obszar:** Dzielnica II Grzegórzki. Nikt z zespołu nie zna Krakowa.

## Posty

- **Q2:** dwa typy: Potrzeba i Inicjatywa. Usterka to jeden z rodzajów Potrzeby.
- **Q4:** brak osobnego kanału o inwestycjach; rozmowa toczy się w Komentarzach.
- **Q9:** przed dodaniem Potrzeby aplikacja pokazuje podobne; Mieszkaniec daje Poparcie zamiast duplikatu.
- **Q17/Q19/Q20:** kolejność = Poparcia + Poziom zagrożenia (Brak / Utrudnienie / Zagrożenie), osobno od Kategorii. AI proponuje, Mieszkaniec może podnieść, obniża tylko Moderator. Zagrożenie życia = Alarm: aplikacja odsyła do 112.
- **Q28:** ekran „Tak zobaczą to inni”. AI tylko proponuje zmiany (Propozycja AI); nic nie zmienia bez zgody Mieszkańca.
- **Q30:** każda Potrzeba ma jedno Miejsce (pinezkę); Potrzeby społeczne mogą być „Dotyczy okolicy”. Podobnych szukamy w ok. 200 m w tej samej Kategorii, a dla „Dotyczy okolicy” w całej dzielnicy.

## Etapy i zaufanie

- **Q10:** statusy Nowa → W toku → Rozwiązana. Rozwiązaną potwierdzają Mieszkańcy, którzy dali Poparcie. → [ADR 0003](adr/0003-trust-from-confirmed-results.md)
- **Q13:** Organizacja z numerem KRS jest sprawdzana w publicznym API KRS (`api-krs.ms.gov.pl`, działa, bez klucza) i dostaje znaczek „Zweryfikowana”. Bez KRS też może działać, bez znaczka.
- **Q14:** Dorobek zamiast gwiazdek. → [ADR 0003](adr/0003-trust-from-confirmed-results.md)
- **Q15:** Organizację prowadzącą wybiera autor Inicjatywy. Głosowanie tylko w pitchu.
- **Q31:** Potrzeba bez reakcji ma napis „czeka od N dni” (widoczny też dla Urzędnika). Po 14 dniach osoby, które dały Poparcie, dostają pytanie „Nikt się nie podjął. Założysz Inicjatywę?”.
- **Q32:** problem, który wraca, to nowa Potrzeba automatycznie połączona ze starą („Wraca: rozwiązana N miesięcy temu”). Stara zostaje Rozwiązana. Dorobek Organizacji nie spada.
- **Q34:** Organizacja prowadząca bez wieści przez 14 dni: Mieszkańcy widzą „brak wieści od 14 dni”, autor może wybrać inną Ofertę prowadzenia. Tylko w pitchu. Czy to obniża Dorobek: **pytanie otwarte**, patrz [open-questions.md](open-questions.md).

## Pomocnicy

- **Q3:** trzy rodzaje Pomocników: Jednostka miejska, Organizacja, Sprawdzone rozwiązanie. Wolontariusze dołączają do Inicjatyw.
- **Q7:** Sprawdzone rozwiązania: lista na start + każda zakończona Inicjatywa staje się nowym.
- **Q8:** Organizacje: ręczna lista ok. 50 z ngo.krakow.pl na demo + samodzielna rejestracja.
- **Q11:** Organizacja ma konto. Jednostka miejska nie: aplikacja zawsze pokazuje, która odpowiada, i jak się z nią skontaktować.
- **Q29:** Jednostkę miejską wskazuje stała tabela Kategoria → Jednostka, nie AI.
- **Q33:** karta Sprawdzonego rozwiązania ma 6 pól: problem, co zrobiono, gdzie, kto, koszt i czas, źródło (link). Bez źródła nie wchodzi na listę. AI sama proponuje pasujące karty przy nowej Potrzebie.

## Droga do miasta

- **Q16:** AI pisze Szkic wniosku o Inicjatywę lokalną. Budujemy. Zadanie Tomasza. → [ADR 0004](adr/0004-draft-local-initiative-not-bypass-city.md)

## Konta, prywatność, AI

- **Q21:** AI sprawdza tekst przed publikacją (obelgi, dane osobowe) i automatycznie rozmywa twarze i tablice.
- **Q22:** przeglądać może każdy; dodawać i popierać tylko po zalogowaniu (e-mail / Google). Jedno Poparcie na osobę. mObywatel tylko w pitchu.
- **Q25:** do rozmywania EgoBlur (twarze + tablice), zapasowo `deface` (tylko twarze). Test: Kacper + Gabriel.
- **Q26:** najpierw rozmycie, potem AI; oryginał kasowany od razu. → [ADR 0005](adr/0005-blur-before-any-ai-sees-a-photo.md)
- **Q24/Q27:** model wybieramy po teście Tomasza (Gemini Flash vs Claude Haiku 4.5 do sortowania, Claude Sonnet 5.5 do Szkicu wniosku). Model da się zmienić jedną linijką. Subskrypcja Claude nie obejmuje API.

## Mapa i powiadomienia

- **Q23:** mapa dla Urzędnika: kropka = Potrzeba, rozmiar = liczba Poparć, kolor = Poziom zagrożenia; z boku 5 najważniejszych Potrzeb z Podsumowaniem dyskusji.
- **Q35:** zakładka „Moje” w aplikacji. Push i e-mail tylko w pitchu.

## Demo

- **Q36:** ok. 30 przykładowych Potrzeb w Grzegórzkach, oznaczonych w bazie jako przykład; w pitchu mówimy o tym wprost. Aplikacja przyjmuje Potrzeby z całego Krakowa, żeby jury mogło dodać Potrzebę na żywo z Tauron Arena (Czyżyny).

## Nazwa, biznes, technologie, zakres

- **Q37:** robocza nazwa **Sąsiedzisko**. Ostateczną wybiera Eryk (po sprawdzeniu nazwy i domeny).
- **Q38:** model biznesowy: start jako pilotaż w jednej dzielnicy za grant, potem abonament płacony przez miasto / rady dzielnic; dla Mieszkańców i Organizacji za darmo. Zadanie Eryka na pitch.
- **Q39/Q40:** React + TypeScript + Leaflet (Patryk), FastAPI, Supabase, serwer z Linuxem. → [ADR 0006](adr/0006-stack-react-fastapi-supabase.md)
- **Q41:** trzy poziomy zakresu, pętla „Inicjatywa → Sprawdzone rozwiązanie” w Poziomie 1. → [scope.md](scope.md)

## Ludzie i czas

- **Q42:** role: Gabriel — lider techniczny, baza, wdrożenie; Patryk — frontend; Kacper — droga zdjęcia, potem frontend z Patrykiem; Szymon — backend (Poparcia, Komentarze, Inicjatywy, statusy); Tomasz — wszystkie funkcje AI; Eryk — pitch, demo, biznes, stoisko HubMI.pl, testy jako mieszkaniec, README. → [BRIEF.md](../BRIEF.md)
- **Q43:** plan to lista kroków, bez godzin. → [event-plan.md](event-plan.md)
- **Q44:** zdjęcia do przykładowych Potrzeb robimy sami, po 5 na osobę, w czwartek lub piątek. → [pre-event-tasks.md](pre-event-tasks.md)
- **Q45:** podział ról na pitchu: **pytanie otwarte**. → [open-questions.md](open-questions.md)

## Zasady HackYeah, o których pamiętamy

- AI wolno używać, ale trzeba to podać. W README będzie sekcja „Użycie AI”.
- Repozytorium musi być publiczne: klucze API tylko w `.env`, dodanym do `.gitignore`.
