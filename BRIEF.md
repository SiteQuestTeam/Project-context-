# Sąsiedzisko — brief dla zespołu

**HackYeah 2026 · 3–4 października · Tauron Arena Kraków · zadanie partnerskie HubMI.pl (15 000 PLN)**

> **W skrócie.** Mieszkańcy Krakowa dodają to, czego brakuje w ich okolicy (**Potrzeby**) i to, co chcą z tym zrobić (**Inicjatywy**).
> AI łączy każdą Potrzebę z tymi, którzy mogą pomóc: odpowiednim urzędem, organizacją społeczną albo sprawdzonym rozwiązaniem z innego miejsca.
> Gdy mieszkańcy się dogadają, AI pisze za nich szkic wniosku do miasta. Każda udana Inicjatywa staje się podpowiedzią dla kolejnych dzielnic.

`Sąsiedzisko` to nazwa robocza.

---

## 1. Dlaczego HubMI.pl, a nie zadanie Krakowa

Zaczynaliśmy od „aplikacji do zgłaszania usterek dla Krakowa”. Po przeczytaniu listy zadań zmieniliśmy kierunek:

- **Zadanie miasta („Cracow without barriers”, 5 000 PLN)** dotyczy dostępności miejsc dla osób z niepełnosprawnościami, nie usterek.
- **Samo zgłaszanie usterek już istnieje.** Aplikacja mKraków ma formularz na dziury i połamane ławki. Innowacyjność to 30% oceny.
- **HubMI.pl (15 000 PLN)** pasuje do naszej części „społecznej” (rozmowy mieszkańców o okolicy), a nagroda jest trzy razy większa.

Rdzeń pomysłu (zdjęcie + miejsce + AI sortuje + mapa) zostaje. Usterka jest teraz jednym z rodzajów Potrzeby.

## 2. Czego chce HubMI.pl

Pełna treść zapowiedzi zadania ze strony HackYeah:

> *How can we ensure that good ideas for solving social problems do not go unnoticed? Use technology to connect residents' needs more effectively with knowledge, proven solutions, and people ready to take action. Create a concept that will help valuable initiatives reach the places where they are needed most and facilitate cooperation between residents, institutions, and social organizations.*

Rozkładamy to na pięć potrzeb:

| # | HubMI.pl chce… |
|---|---|
| **H1** | żeby **dobre pomysły** na problemy społeczne **nie przepadały** |
| **H2** | połączyć **potrzeby mieszkańców** z **wiedzą i sprawdzonymi rozwiązaniami** |
| **H3** | połączyć je z **ludźmi gotowymi działać** |
| **H4** | żeby wartościowe inicjatywy **trafiały tam, gdzie są najbardziej potrzebne** |
| **H5** | **współpracy** mieszkańców, **instytucji** i **organizacji społecznych** |

Uwaga: zadanie mówi „create a **concept**”. Liczy się pomysł i jego sensowność, a działający prototyp go uwiarygadnia.
Pełna treść zadania i jego zasady oceny pojawią się dopiero, gdy zadania się odblokują. Wtedy sprawdzamy, czy coś się nie zmieniło.

## 3. Jak Sąsiedzisko odpowiada na każdą z nich

| HubMI.pl | Nasza odpowiedź |
|---|---|
| **H1** dobre pomysły nie przepadają | Każda zakończona **Inicjatywa** sama staje się **Sprawdzonym rozwiązaniem**, które aplikacja podpowiada w innych dzielnicach. Pomysł, który zadziałał w jednym miejscu, nie ginie. |
| **H2** potrzeby ↔ wiedza | Przy każdej nowej Potrzebie AI pokazuje pasujące **karty Sprawdzonych rozwiązań**: co zrobiono, gdzie, kto, za ile, ze źródłem. |
| **H3** potrzeby ↔ ludzie | **Organizacje** zgłaszają się do prowadzenia Inicjatyw, **mieszkańcy** dołączają jako wolontariusze albo dają **Poparcie**. |
| **H4** inicjatywy trafiają tam, gdzie trzeba | **Mapa dla urzędnika** pokazuje, gdzie zbierają się Potrzeby, ile mają Poparć i jak są groźne. Potrzeby „bez reakcji” są wyraźnie oznaczone. |
| **H5** mieszkańcy + instytucje + organizacje | Każda Potrzeba pokazuje **odpowiedzialny urząd**. Droga do miasta idzie przez prawdziwą procedurę **Inicjatywy lokalnej**, a AI pisze **szkic wniosku**. |

## 4. Jak to działa: historia na demo

1. **Pani Zofia dodaje Potrzebę:** „Brak ławek przy ul. X, seniorzy nie mają gdzie odpocząć” + zdjęcie.
2. **AI od razu pokazuje:** kategorię, poziom zagrożenia, odpowiedzialny urząd, podobne Potrzeby w pobliżu i kartę Sprawdzonego rozwiązania.
3. **30 sąsiadów daje Poparcie** i rozmawia w komentarzach.
4. **AI robi Podsumowanie dyskusji:** z czym się zgadzają, o co się spierają.
5. **Ktoś zakłada Inicjatywę** „3 ławki przy ul. X”.
6. **Organizacje zgłaszają się** do prowadzenia. Autor wybiera jedną, widząc jej dorobek.
7. **AI pisze szkic wniosku** o Inicjatywę lokalną.
8. **Ławki stoją. Mieszkańcy potwierdzają.** Inicjatywa staje się Sprawdzonym rozwiązaniem dla innych dzielnic.
9. **Ostatni ekran: mapa dla urzędnika.**

Demo pokazujemy na Dzielnicy II Grzegórzki, ale aplikacja działa w całym Krakowie. Jury może dodać Potrzebę na żywo z hali.
Szczegóły: [docs/demo-scenario.md](docs/demo-scenario.md).

## 5. Pomysły, na których stoi projekt

**Dwa typy postów.** *Potrzeba* (coś jest źle albo czegoś brakuje: od zepsutej latarni po samotnych seniorów) i *Inicjatywa* (pomysł albo działanie, które na nią odpowiada).

**Poparcie zamiast duplikatów.** Zanim ktoś doda Potrzebę, widzi podobne w pobliżu i może kliknąć „Popieram”. Liczba Poparć mówi, co jest najważniejsze.

**Trzech Pomocników.** Każda Potrzeba dostaje propozycje:
- **Jednostka miejska**: urząd, który za to odpowiada. Bierze się ze stałej tabeli, AI go nie zgaduje.
- **Organizacja**: NGO, klub, grupa parafialna.
- **Sprawdzone rozwiązanie**: karta z 6 polami (problem, co zrobiono, gdzie, kto, koszt i czas, **źródło**). Bez źródła karta nie wchodzi.

**Papiery pisze AI, ale ich nie omija.** Organizacja nie postawi ławki na miejskim terenie bez zgody miasta. Istnieje jednak procedura **Inicjatywy lokalnej**: mieszkańcy (sami albo przez NGO) składają wniosek i robią coś razem z miastem. Miasto samo podaje montaż ławek jako przykład, a wnioski przyjmuje przez cały rok. AI składa szkic takiego wniosku z Potrzeby, komentarzy i Poparć.

**Zaufanie z faktów, nie z gwiazdek.** Organizacja ma **Dorobek**: liczbę Inicjatyw, które mieszkańcy potwierdzili jako zrobione. Potrzebę jako „Rozwiązaną” potwierdzają mieszkańcy, nie sama organizacja. Organizacja z numerem KRS dostaje znaczek „Zweryfikowana”. Sprawdzamy to w publicznym API rejestru KRS: jest darmowe i przetestowane.

**Zagrożenie osobno od tematu.** Każda Potrzeba ma *Kategorię* (czego dotyczy) i *Poziom zagrożenia* (Brak / Utrudnienie / Zagrożenie). Otwarta studzienka jest wyżej niż ładna ławka z 50 Poparciami. AI proponuje poziom, mieszkańcy mogą go podnieść, obniżyć może tylko moderator. Zagrożenie życia (pożar, gaz, ranny) to **Alarm**: aplikacja nie wrzuca go do kolejki, tylko każe dzwonić na 112.

**Prywatność od pierwszego kroku.** Każde zdjęcie jest najpierw automatycznie rozmywane na naszym serwerze (twarze i tablice, narzędzie EgoBlur od Meta). Dopiero rozmyta wersja trafia do AI. Oryginał jest od razu kasowany. **Żadna twarz nie trafia do Google ani Anthropic.**

**AI tylko proponuje.** AI może zasugerować lepszy tytuł albo kategorię, ale nic nie zmienia bez zgody mieszkańca.

## 6. Czego świadomie nie robimy

- **Nie udajemy integracji z urzędami.** Urzędy nie mają kont; pokazujemy, który odpowiada i jak się z nim skontaktować.
- **Nie ma ocen gwiazdkowych** organizacji.
- **Nie ma aplikacji w sklepie.** Robimy jedną PWA: stronę, którą można dodać do ekranu telefonu jak aplikację.
- **Nie ma osobnego kanału o inwestycjach.** Rozmowa toczy się pod Potrzebami i Inicjatywami.
- **Nie obsługujemy zgłoszeń alarmowych.** Od tego jest 112.

## 7. Jak jury nas oceni

Ogólne kryteria HackYeah (zadanie HubMI.pl może mieć własne, sprawdzamy na miejscu):

| Kryterium | Waga | Nasz atut |
|---|---|---|
| Pomysł i innowacyjność | 30% | pętla „Inicjatywa → Sprawdzone rozwiązanie”, AI piszące wniosek |
| Związek z zadaniem | 20% | każda z pięciu potrzeb HubMI.pl ma odpowiedź (tabela w pkt 3) |
| Praktyczna użyteczność | 20% | prawdziwa procedura miasta, publiczny rejestr KRS, model biznesowy |
| Design | 20% | React + gotowe komponenty, mapa, demo na telefonie |
| Kompletność | 10% | działająca droga od Potrzeby do mapy |

**Model biznesowy:** dla mieszkańców i organizacji za darmo. Start: pilotaż w jednej dzielnicy za grant. Potem abonament płacony przez miasto albo rady dzielnic, które dostają mapę Potrzeb i gotowe szkice wniosków.

## 8. Kto co robi

| Osoba | Zadanie na hackathonie |
|---|---|
| **Gabriel** | lider techniczny: baza (Supabase, wyszukiwanie w promieniu), dane przykładowe, wdrożenie |
| **Patryk** | frontend: React + TypeScript + Leaflet, wszystkie ekrany, mapa, PWA |
| **Kacper** | droga zdjęcia (wysyłka → rozmycie → zapis), potem frontend z Patrykiem |
| **Szymon** | backend (FastAPI): Poparcia, Komentarze, Inicjatywy, Oferty, statusy |
| **Tomasz** | funkcje AI: sortowanie, podobne Potrzeby, karty rozwiązań, Podsumowanie dyskusji, szkic wniosku |
| **Eryk** | pitch, historia demo, model biznesowy, rozmowa ze stoiskiem HubMI.pl, testy „jak mieszkaniec”, README |

**Technologie:** React + TypeScript + Leaflet · FastAPI (Python) · Supabase (baza z mapami, logowanie, zdjęcia) · serwer z Linuxem · model AI wybrany po teście (Gemini Flash albo Claude).

## 9. Co dalej

- **Przed wyjazdem** (czwartek–piątek): [docs/pre-event-tasks.md](docs/pre-event-tasks.md). Każdy robi **5 zdjęć prawdziwych problemów** do danych przykładowych.
- **Na hackathonie, krok po kroku:** [docs/event-plan.md](docs/event-plan.md).
- **Co budujemy, a co tylko w pitchu:** [docs/scope.md](docs/scope.md).
- **Do omówienia w zespole:** [docs/open-questions.md](docs/open-questions.md).

## Słowniczek i decyzje

- [CONTEXT.md](CONTEXT.md): wszystkie pojęcia (Potrzeba, Poparcie, Dorobek…) z polskimi nazwami do aplikacji. Używajmy tych słów w kodzie i na pitchu.
- [docs/grilling-decisions.md](docs/grilling-decisions.md): lista wszystkich ustaleń.
- [docs/adr/](docs/adr/): większe decyzje z uzasadnieniem.

## Zasady HackYeah, o których pamiętamy

- **AI wolno używać, ale trzeba to podać.** W README będzie sekcja „Użycie AI”. Pomysł musi być nasz.
- **Repozytorium musi być publiczne.** Klucze API tylko w `.env`, nigdy w kodzie.

---

**Źródła:** [zadania HackYeah 2026](https://hackyeah.pl/tasks-prizes) · [regulamin](https://hackyeah.pl/rules?lang=en) · [AI na HackYeah](https://hackyeah.pl/news/how-to-use-ai-responsibly-at-a-hackathon-uxv05) · [Inicjatywa lokalna w Krakowie](https://www.krakow.pl/aktualnosci/278957,26,komunikat,zglos_projekt_w_ramach_inicjatywy_lokalnej.html) · [baza organizacji ngo.krakow.pl](https://ngo.krakow.pl/2911,ma,0,artykul,organizacje_pozarzadowe.html) · [aplikacja mKraków](https://www.krakow.pl/282944,artykul,o-aplikacji-mkrakow.html) · [EgoBlur](https://github.com/facebookresearch/EgoBlur)
