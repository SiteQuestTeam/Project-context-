# SideQuest — brief dla zespołu (wersja 3, zadanie Smart City)

**HackYeah 2026 · 3–4 października · Tauron Arena Kraków · zadanie SMART CITY (PKO), nagroda 8 000 PLN**

> **W skrócie.** Pokémon Go, ale dla działań społecznych.
> Młodzi dorośli wychodzą z domu i robią prawdziwe rzeczy dla swojej okolicy: znajdują problemy (**Zwiad**), pomagają ludziom (**Misje**, solo albo w grupie) i wspólnie zmieniają miejsca (**Rajdy**).
> Szare miejsca na mapie robią się zielone, gdy problem znika.
> Gracze zbierają **Punkty**, **Odznaki** i **Rangi**, chwalą się nimi w social mediach, a ich dzielnice walczą w **Lidze dzielnic**.
> Lokalne firmy dają **Nagrody** (np. darmową kawę).
> Miasto po raz pierwszy widzi, **kto naprawdę działa** i **które problemy ludzie naprawdę potwierdzili na miejscu**.

Nazwa aplikacji: **SideQuest**. Nazwy w grze (Zwiad, Misja, Rajd…) są robocze; ostateczne wybiera zespół psychologiczny.

**Termin oddania: niedziela 4 października, przyjmujemy 11:00 rano** (regulamin pisze „11:00 PM”, pytamy mentora). Oddajemy wcześniej, nie w ostatniej minucie.

---

## 1. Problem (slajd 1)

> **Młodzi dorośli w Krakowie nie znają swoich sąsiadów i nie biorą udziału w życiu okolicy. Nieliczni, którzy działają, są niewidoczni, więc rady dzielnic zapełniają politycy, a nie ludzie, którzy coś robią.**

Mentorzy PKO chcą jednego konkretnego problemu społecznego, nie ogólnej platformy. To jest nasz problem.

## 2. Dlaczego Smart City, a nie HubMI.pl

ROPS (HubMI.pl) nie chce oddolnych inicjatyw mieszkańców, a prawa do kodu przeszłyby na nich. Smart City ma w zakresie „komunikację między mieszkańcami a instytucjami”, takie same kryteria, a **prawa autorskie zostają u nas**. Szczegóły: [ADR 0007](docs/adr/0007-smart-city-task-not-hubmi.md).
Stary rdzeń (Potrzeby, Pomocnicy, szkic wniosku) odpada. Robimy grę: [ADR 0008](docs/adr/0008-game-replaces-hubmi-core.md).

## 3. Jak działa gra

Pojęcia pisane wielką literą: [CONTEXT.md](CONTEXT.md).

**Gracz** wybiera przy rejestracji swoją **Dzielnicę** (jedną z 18).

### Trzy klasy akcji

Różnica między Misją a Rajdem: **czy zmienia się miejsce**, a nie „solo czy w grupie”.

| Klasa | Co robi | Przykład | Dowód |
|---|---|---|---|
| **Zwiad** | pokazuje problem (pasywnie), naprawia ktoś inny | przy bloku jest rura, do której ludzie przypinają rowery → „brakuje stojaka” | **Zdjęcie na żywo** w tym miejscu |
| **Misja** | pomaga ludziom albo okolicy, **bez zmiany miejsca**, solo albo w grupie | solo: pomóż sąsiadce wnieść zakupy; w grupie: pomagamy seniorom ustawić telefony w bibliotece | solo: zdjęcie + GPS; w grupie: **Odbicie** (skan kodu) |
| **Rajd** | **zmienia miejsce**, w grupie, zwykle z Szarego miejsca | sprzątanie skweru | Odbicia + zdjęcie „przed” → Rajd → zdjęcie „po” |

- **Zdjęcie na żywo:** tylko aparat w aplikacji, bez galerii, GPS do ok. 50 m od miejsca. Trzeba się pofatygować na miejsce.
- **Trudność** wylicza aplikacja, nie Organizator (inaczej każdy wybrałby najwyższą). Weryfikator może ją zmienić o jeden poziom:

| Poziom | Co |
|---|---|
| **Miedź** | Zwiad, Potwierdzenie, akcja do 15 min |
| **Srebro** | do 1 h |
| **Złoto** | do 2 h |
| **Platyna** | 2–4 h |
| **Diament** | Rajd, który zamienia Szare miejsce w zielone |

Wyższy poziom daje więcej Punktów.

### Szare miejsca

- **Zwiad tworzy Szare miejsce** na mapie.
- Inni Gracze mogą tam pójść i je **Potwierdzić** swoim Zdjęciem na żywo. **Nie da się poprzeć z kanapy.** Potwierdzenie zapisuje się w Historii Gracza.
- Szare miejsce ma pole **„Kto naprawi”**: **Miasto / Gildia / Gracze**. Przy Zwiadzie aplikacja zadaje 2 pytania tak/nie, zawsze w tej kolejności:
  1. „Czy to teren lub sprzęt miasta, albo potrzebna jest zgoda lub pieniądze miasta?” → **Miasto**
  2. „Czy trzeba specjalnych umiejętności albo narzędzi (spawanie, prąd, praca na wysokości)?” → **Gildia**
  3. Oba „nie” → **Gracze**

  Weryfikator może poprawić wynik. Przykład: stojak na miejskim chodniku → Miasto (które może zlecić go Gildii). Stojak na terenie spółdzielni → Gildia. Śmieci na skwerze → Gracze. Poziom 2: AI patrzy na zdjęcie i miejsce i podpowiada odpowiedź. Pitch: mapa gruntów miasta i nauka z wcześniejszych projektów.
  - **Gracze:** przycisk „Załóż Rajd”, a zdjęcie „przed” już jest.
  - **Gildia:** potrzebne umiejętności, których zwykły Gracz nie ma (np. spawanie stojaka). Gildia to wspólna nazwa dla wielu organizacji (rzemieślnicy, NGO, firmy). W wersji demo to tylko etykieta.
  - **Miasto:** trafia do Widoku dla miasta.
- Gdy problem znika, ktoś robi zdjęcie „po”. **Miejsce robi się zielone.** Mapa dzielnicy powoli zmienia się z szarej w zieloną.

### Akcje grupowe (Misje grupowe i Rajdy)

- Zakłada je każdy Gracz albo sam **Hub** (prawdziwe miejsce publiczne, np. biblioteka, dom kultury).
- Mają godzinę startu, długość, minimalną liczbę osób i **Role** z miejscami (np. „kierowca 0/1”, „fotograf 2/3”). Gdy brakuje ludzi, mapa pokazuje „brakuje N”. Widać, kto już dołączył: „Ola, Kuba i 7 innych”.
- Każdy uczestnik skanuje kod **Organizatora** na miejscu (**Odbicie**).
- W Rajdzie Organizator robi też zdjęcie „przed” i „po” **samego miejsca**.
- Po Rajdzie powstaje **Karta Rajdu**: przed → po, liczba osób, godziny i **Rzadkość**: **Zwykły** (do 5 osób), **Rzadki** (5–15), **Epicki** (ponad 15 albo Szare miejsce zrobiło się zielone).
- **Znajomi:** po Rajdzie możesz dodać ludzi, którzy tam byli. Tak poznajesz sąsiadów. (Nazwa do wymyślenia.)

### Postęp

- **Punkty** tylko za potwierdzone działania, według Trudności. Za klikanie, polubienia, zaproszenia i rejestrację: zero. Premia dla Organizatora, gdy jego akcja zbierze minimum osób.
- **Ranga:** jedna, rośnie po progach Punktów. Daje wiarygodność, nie władzę. Na najwyższych Rangach można zostać Weryfikatorem. Osobne ścieżki (Ekologia, Kultura…) tylko w pitchu.
- **Odznaki** za konkretne osiągnięcia, np. „Iskra”: 10 osób dołączyło do twojego Rajdu.
- **Historia:** profil pokazuje wszystkie akcje, w których Gracz brał udział, osobno Zwiady, Misje i Rajdy. Należy do człowieka i zostaje, gdy zmieni dzielnicę.
- **Bez serii (streaków) i bez presji.** Kto wraca po miesiącu, widzi „Witaj ponownie, oto 3 proste akcje obok ciebie”.
- **Karta do udostępnienia:** nowa Odznaka, Ranga albo Karta Rajdu to gotowy obrazek na Instagram story. **Ludzie lubią się chwalić**: to nasza darmowa reklama.
- **Nagrody** odblokowują się po Randze albo Odznace. Nie kupuje się ich za Punkty. Prawdziwe od lokalnych **Sponsorów** (darmowa kawa) albo kosmetyczne (tytuł „Animator Dzielnicy”, ramka avatara). Dzielnica, która wygra Ligę, odblokowuje swoim aktywnym Graczom „Pucharowy rabat”.
- **Liga dzielnic:** potwierdzone godziny działań **na 1000 mieszkańców**, więc mała dzielnica może wygrać z dużą. **Sezon** trwa miesiąc i się resetuje. Sezon może mieć temat (np. „Seniorzy”): daje specjalną Odznakę i wyróżnione Misje, ale nie zmienia liczenia godzin.

## 4. Jak nie dajemy się oszukać

Jury na pewno zapyta „a jak ktoś oszukuje?”.

- **Kod akcji grupowej zmienia się co 30 sekund** i działa tylko na miejscu (GPS). Zrzut ekranu wysłany koledze do domu nie działa.
- **Zdjęcie na żywo:** tylko z aparatu w aplikacji, na miejscu.
- **Weryfikatorzy:** Gracze z najwyższą Rangą sprawdzają Dowody (nigdy ludzi). Każdy Dowód trafia do 3 Weryfikatorów, 2 muszą się zgodzić. Weryfikator, który często się nie zgadza z innymi, traci to prawo. Pokémon Go robi to samo z nowymi PokéStopami (program Wayfarer).
- **Punkty w weryfikacji:** za Misję solo czekają na Weryfikatorów. Za Odbicie przychodzą od razu, ale w Rajdzie znikają, gdy Weryfikatorzy odrzucą zdjęcia „przed/po”.
- **Dzienny limit Punktów** (Poziom 2).
- **Prywatność:** zdjęcia Misji solo widzą tylko Weryfikatorzy i kasujemy je po sprawdzeniu. Zdjęcia „przed/po” z Rajdu pokazują samo miejsce: Weryfikatorzy sprawdzają, że nie ma na nich twarzy, i dopiero wtedy są publiczne. Profil pokazuje pseudonim, nie imię i nazwisko.

## 5. Co dostaje miasto

**Widok dla miasta:**
- **Szare miejsca do naprawy przez miasto**, od najczęściej Potwierdzanych. To lista problemów sprawdzonych na miejscu przez ludzi, a nie skarg z kanapy.
- Mapa Ligi dzielnic i najbardziej aktywne Huby.
- Najaktywniejsi Organizatorzy w każdej dzielnicy (tylko ci, którzy się zgodzili).

**Aktywność ma być informacją dla samorządu:** rada dzielnicy widzi, kto naprawdę działa, a nie kto najgłośniej mówi.

## 6. Historia na demo

Ola, 24 lata, nowa w Grzegórzkach: Zwiad (rura zamiast stojaka) → Misja grupowa w bibliotece (pomoc seniorom z telefonami, poznaje ludzi) → Rajd: sprzątanie skweru, Szare miejsce robi się zielone (Diament, Epicka Karta Rajdu) → nowa Ranga → Nagroda → dzielnica w górę Ligi → Widok dla miasta. Na żywo jury skanuje kod Misji grupowej w Hubie „Tauron Arena”.
Szczegóły: [docs/demo-scenario.md](docs/demo-scenario.md).

## 7. Jak jury nas oceni

| Kryterium | Waga | Nasz atut |
|---|---|---|
| Pomysł i innowacyjność | 30% | gra jak Pokémon Go, ale Punkty tylko za prawdziwe działania; „nie da się poprzeć z kanapy”; szara mapa robi się zielona; Liga dzielnic na 1000 mieszkańców |
| Związek z zadaniem | 20% | Huby to miejskie przestrzenie, które lepiej wykorzystujemy; Szare miejsca i Widok dla miasta = komunikacja mieszkańcy ↔ instytucje |
| Praktyczna użyteczność | 20% | działa na telefonie z linku; ochrona przed oszustwem; Sponsorzy płacą Nagrodami |
| Design | 20% | szara → zielona mapa, Karta Rajdu „przed/po”, Odznaki, Liga. Mile widziane: duży kontrast, duży tekst, lista obok mapy (dostępność) |
| Kompletność | 10% | cała historia Oli działa od początku do końca |

**Model biznesowy (pitch):** dla Graczy za darmo. Sponsorzy płacą Nagrodami za ruch i reklamę. Miasto płaci za Widok dla miasta (potwierdzone problemy i dane o aktywności w dzielnicach). Slajd z kosztem utrzymania.

## 8. Kto co robi

| Zespół | Osoba | Zadanie |
|---|---|---|
| Techniczny | **Gabriel** | baza, Punkty i Liga, dane przykładowe, hosting |
| Techniczny | **Szymon** | serwer: Zwiady, Misje, Rajdy, Odbicia, Punkty, Weryfikacja, Widok dla miasta |
| Techniczny | **Patryk** | aplikacja: wszystkie ekrany, mapa, aparat, skaner kodu |
| Psychologiczny | **Eryk, Tomasz, Kacper** | zasady gry (Punkty, poziomy Trudności, progi Rang, lista Odznak), lista Misji, tematy Sezonów, 3 Sponsorzy, nazwy, PDF 10 slajdów, pitch, test z ludźmi na hali |

## 9. Technologie i plan

Technologie wybiera zespół techniczny, dokumenty się do nich dostosowują ([ADR 0009](docs/adr/0009-tech-team-owns-the-stack.md)). Teraz: `SiteQuestTeam/App` (Expo) i `SiteQuestTeam/Backend` (NestJS). Jedyny warunek: jury otwiera aplikację z linku na swoim telefonie. Bez AI w podstawowej wersji.
**Wszystkie Punkty liczy serwer, nigdy telefon.**
Kolejne kroki: [docs/event-plan.md](docs/event-plan.md). Co budujemy, a co tylko w pitchu: [docs/scope.md](docs/scope.md).

## 10. Co oddajemy

Obowiązkowo: tytuł, nazwa zespołu, lista członków, opis projektu, **PDF max 10 slajdów**. Opcjonalnie: repozytorium, link do demo, zrzuty ekranu, film.
**PDF musi się bronić bez nas**: w etapie 1 mentorzy czytają go sami. Pitch na żywo dopiero w finale.

## 11. Zasady HackYeah, o których pamiętamy

- AI wolno używać, ale trzeba to podać. W README sekcja „Użycie AI”.
- Musimy umieć wyjaśnić każdą decyzję techniczną, także kod napisany z AI.
- Repozytorium publiczne: klucze tylko w `.env` (w `.gitignore`).
- Oddzielamy pracę z hackathonu od rzeczy zrobionych wcześniej.

## 12. Otwarte sprawy

Żadna nie blokuje budowy:
- Gildia: jak działa naprawdę (konta, które organizacje). Na demo tylko etykieta.
- Nazwa dla znajomych, ostateczne nazwy w grze: zespół psychologiczny.
- Dokładne dane przykładowe, progi Rang, liczby Punktów, ile Punktów za każdy poziom Trudności, Sponsorzy: zespół psychologiczny + Gabriel.
- Pytania do mentora PKO: platforma zgłoszeń (Challenge Rocket czy Hack Tribe) i godzina końca.

Wszystkie decyzje z grillowania: [docs/grill-smart-city.md](docs/grill-smart-city.md).
