# Inspiracje: podobne aplikacje i czego się od nich uczymy

Research z 1 października 2026. Pojęcia: [CONTEXT.md](../CONTEXT.md).
Każda pozycja: co robi, co bierzemy (albo czego unikamy). Zrzuty ekranu robimy sami z linków.

## Najważniejsze wnioski (do pitchu)

1. **Zgłaszanie usterek jest rozwiązane.** FixMyStreet, SeeClickFix, Traffy Fondue, NaprawmyTo, Warszawa 19115, mKraków. Nie konkurujemy z nimi. Nasza nowość jest dalej: od Potrzeby do Inicjatywy i z powrotem do Sprawdzonego rozwiązania.
2. **Nie znaleźliśmy narzędzia, które pisze wniosek o Inicjatywę lokalną.** Warszawa, Gdynia i Kraków przyjmują papierowy formularz albo ePUAP. Sprawdzone: strony miast i wyszukiwarka. To nasz najmocniejszy wyróżnik (H5).
3. **Kraków ma bardzo mało Inicjatyw lokalnych.** W jednym roku: 27 wniosków, 22 zrealizowane. W 2023 r. 17 projektów. Procedura istnieje, ale ludzie z niej nie korzystają. Mamy liczbę do pitchu.
4. **Biblioteki „sprawdzonych rozwiązań” istnieją, ale tylko dla urzędników** (Bloomberg, OECD OPSI, dobrepraktyki.pl). Nikt nie podaje ich mieszkańcowi w chwili, gdy zgłasza problem. To dokładnie nasze H2.
5. **„Podsumowanie dyskusji” ma mocne wzorce:** Talk to the City, Jigsaw Sensemaker, Pol.is. Możemy powiedzieć jury, że idziemy drogą, którą sprawdził Tajwan i Google.
6. **Uwaga na trwałość.** NaprawmyTo.pl zamknięto po 8 latach. Jury może zapytać „kto za to zapłaci za 3 lata”. Odpowiedź: model biznesowy z BRIEF.md (abonament miasta).

## 1. Zgłaszanie problemów do miasta (nasz punkt startu, nie konkurencja)

| Aplikacja | Link | Co robi | Co bierzemy |
|---|---|---|---|
| **FixMyStreet** (UK, mySociety) | [fixmystreet.com](https://www.fixmystreet.com/) · [kod](https://github.com/mysociety/fixmystreet) | Pinezka + zdjęcie, raport idzie do właściwej rady. Przed zgłoszeniem pokazuje podobne w pobliżu ([opis](https://www.societyworks.org/2024/04/02/you-can-now-customise-fixmystreet-pros-duplicate-report-radius-per-category/)). | **Promień szukania podobnych zależy od Kategorii.** Dziura w drodze: 50 m. Park: 300 m. U nas teraz stałe 200 m (Q30). Łatwa poprawka. Na telefonie pokazują małą mapkę przy duplikacie. |
| FixMyStreet Brussels | [be.brussels](https://be.brussels/en/transport-mobility/road-safety/fixmystreet-report-incident-or-unsafe-situation) | Ta sama idea w Brukseli. | **Ostrzeżenie:** [badanie](https://www.researchgate.net/publication/316030107_FixMyStreet_Brussels_Socio-Demographic_Inequality_in_Crowdsourced_Civic_Participation) pokazuje, że bogatsze dzielnice zgłaszają więcej. Liczba Poparć nie równa się potrzebie. Argument dla naszej mapy Urzędnika: pokazać też „ciche” dzielnice (H4). |
| FixMyStreet (status) | [open311](https://www.fixmystreet.com/open311) | Każdy może kliknąć „naprawione”. | **Unikamy.** U nas „Rozwiązana” potwierdzają tylko osoby, które dały Poparcie (ADR 0003). Mówimy to jury jako przewagę. |
| **SeeClickFix** (USA, CivicPlus) | [wiki](https://en.wikipedia.org/wiki/SeeClickFix) · [AI 2026](https://www.civicplus.com/news/nn/civicplus-announces-ai-capabilities-with-six-new-intelligent-product-releases/) | Od stycznia 2026 AI czyta zdjęcie i proponuje kategorię. Urzędnik może scalić duplikaty. | Potwierdza, że AI → Kategoria ze zdjęcia to dziś standard. Nie sprzedajemy tego jako nowości. |
| **Traffy Fondue** (Tajlandia) | [wiki](https://en.wikipedia.org/wiki/Traffy_Fondue) · [NSTDA](https://www.nstda.or.th/en/news/news-years-2026/thailand%E2%80%99s-ai-powered-citizen-report-platform.html) | Zgłoszenie przez LINE. AI klasyfikuje i kieruje do właściwego urzędu. 1,37 mln zgłoszeń, 77% rozwiązanych. | Dowód skali dla pitchu. Różnica: u nas urząd wybiera tabela, nie AI (Q29). |
| **NaprawmyTo.pl** (Fundacja Stocznia) | [PZR](https://www.pzr.org.pl/naprawmy-to/) · [PAP](https://samorzad.pap.pl/kategoria/jak-robia-inni/naprawmy-aplikacja-naprawmytopl-w-katowicach-mieszkancy-zglaszaja-miasto) | Polska wersja FixMyStreet. 30 miast, w Katowicach 29 tys. zgłoszeń. Zamknięty po 8 latach, Katowice przeszły na własną aplikację. | Lekcja o trwałości (patrz wnioski). Fundacja Stocznia to dobry kontakt: zna temat i robi innowacje społeczne. |
| **Warszawa 19115** | [warszawa19115.pl](https://warszawa19115.pl/en/-/opis-funkcji-aplikacji-mobilnej-warszawa-19115) | Zgłoszenie w 3 krokach, numer sprawy, „Moje zgłoszenia”, mapa cudzych zgłoszeń. | Wzór zakładki „Moje” (Poziom 2). |
| **mKraków** | [zdmk.krakow.pl](https://zdmk.krakow.pl/nasze-dzialania/miasto-w-twoim-zasiegu-pobierz-aplikacje-mkrakow/) | „Zgłoś problem / Wyślij pomysł”, status zgłoszenia. Także głosowanie w budżecie obywatelskim. | Nasz punkt odniesienia w pitchu: „mKraków przyjmuje usterkę. My prowadzimy ją do rozwiązania z sąsiadami.” |

## 2. Rozmowa mieszkańców i Poparcia

| Aplikacja | Link | Co robi | Co bierzemy |
|---|---|---|---|
| **Commonplace** (UK) | [blog o „Agree”](https://www.commonplace.is/blog/social-proof) · [heatmapa](https://www.commonplace.is/product-roadmap/new-digital-mapping-feature-to-engage-communities) | Pinezka + komentarz na mapie. Można tylko **zgodzić się**, nie można się nie zgodzić. Mapa cieplna dla urzędu. | Potwierdza nasze Poparcie bez „nie popieram”. Heatmapa = pomysł na mapę Urzędnika. |
| **Better Reykjavík / Your Priorities** (Islandia) | [Citizens Foundation](https://www.citizens.is/portfolio_page/better_reykjavik/) · [Participedia](https://participedia.net/case/5320) | Mieszkańcy dodają pomysły, piszą argumenty **za** i **przeciw** w dwóch kolumnach. Ok. 700 pomysłów zrealizowanych przez miasto. Używają AI. | Dwie kolumny „za / przeciw” = prosty wygląd dla Podsumowania dyskusji. Liczba 700 do pitchu: to działa od 2010 r. |
| **Decidim** (Barcelona) | [funkcje](https://decidim.org/features/) · [progi](https://github.com/decidim/decidim/issues/2276) | Propozycje przechodzą do kolejnego etapu po progu poparć. | Pomysł: po N Poparciach aplikacja proponuje „Załóż Inicjatywę”. Pasuje do Q31. |
| **Consul / Decide Madrid** | [porównanie](https://democracy-technologies.org/participation/decide-madrid-and-consul/) | Propozycje + budżet partycypacyjny. Otwarty kod. | Tylko kontekst. Kraków ma już budżet obywatelski ([budzet.krakow.pl](https://budzet.krakow.pl/)). |
| **Nextdoor** (USA) | [Help Map](https://techcrunch.com/2020/03/19/nextdoor-adds-help-maps-and-groups-to-connect-neighbors-during-the-coronavirus-outbreak) | Mapa sąsiadów, którzy oferują pomoc (zakupy, telefon do seniora). | Pomysł na pitch: Wolontariusze widoczni na mapie przy Potrzebach „Dotyczy okolicy” (np. samotni seniorzy). |
| **nebenan.de** (Niemcy) | [Google Play](https://play.google.com/store/apps/details?id=de.nebenan.app&hl=en) | 3 mln użytkowników, wydarzenia, wymiana, grupy. | Tylko kontekst: sąsiedzkie aplikacje działają w Europie. |
| **Hoplr** (Belgia, Holandia) | [dla gmin](https://services.hoplr.com/) · [nowości](https://blog.hoplr.com/en/hoplr-is-renewed-new-features-since-october-2025/) | Sieć sąsiedzka **płacona przez gminy**. 32% gospodarstw w okolicy używa jej co tydzień. Gmina robi ankiety. | **Najlepszy dowód dla naszego modelu biznesowego:** gminy już płacą za taki produkt. Opcja „pokaż też sąsiednie osiedla” pasuje do „Dotyczy okolicy”. |
| Polskie aplikacje osiedlowe | [Helpi](https://helpi-app.pl/) · [e-Osiedle](https://www.eosiedle.pl/) · [OsiedleApp](https://osiedleapp.pl/) · [Po sąsiedzku](https://apps.apple.com/pl/app/po-s%C4%85siedzku/id6764361206) | Ogłoszenia, pomoc sąsiedzka, sprawy wspólnoty mieszkaniowej. | Nie łączą z miastem ani z NGO. To nasza różnica. |

## 3. AI, które streszcza rozmowę (wzór dla Podsumowania dyskusji)

| Narzędzie | Link | Co robi | Co bierzemy |
|---|---|---|---|
| **Talk to the City** (AI Objectives Institute) | [strona](https://ai.objectives.institute/talk-to-the-city) · [blog](https://ai.objectives.institute/blog/talk-to-the-city-an-open-source-ai-tool-to-scale-deliberation) | Otwarty kod. Grupuje opinie w tematy. **Każde zdanie streszczenia ma link do oryginalnego cytatu.** Użyte na Tajwanie i w ONZ. | **Bierzemy zasadę cytatu:** każdy punkt Podsumowania pokazuje 1–2 Komentarze, z których pochodzi. Chroni przed zmyśleniem przez AI. |
| **Jigsaw Sensemaker** (Google) | [GitHub](https://github.com/Jigsaw-Code/sensemaking-tools) · [dokumentacja](https://jigsaw-code.github.io/sensemaking-tools/docs/) | Otwarta biblioteka (TypeScript, Gemini). Tematy → przypisanie komentarzy → streszczenie „zgoda / spór”. Bowling Green: 8000 osób. | Nasz podział „zgadzają się / spierają się” to dokładnie ich wynik. Warto przejrzeć ich prompty przed pisaniem naszego. |
| **Pol.is** (vTaiwan) | [Participedia](https://participedia.net/en/methods/polis) | Ludzie klikają „zgadzam się / nie / pomiń” przy krótkich zdaniach. Algorytm szuka zdań, które łączą grupy. | Tylko w pitchu: przyszły tryb dla dużych sporów. |
| **Go Vocal** (dawniej CitizenLab) | [Sensemaking](https://www.govocal.com/en-uk/platform-features/sensemaking) · [trendy 2026](https://www.govocal.com/trends-report-2026) | Płatna platforma dla 500 miast (Wiedeń, Kopenhaga). AI grupuje opinie. Wiedeń: 2500 opinii przeanalizowanych w kilka godzin. | Dowód, że miasta płacą za analizę AI. Ich raport o trendach to dobre źródło do pitchu. |

## 4. Biblioteki sprawdzonych rozwiązań (wzór dla kart i źródło danych na start)

| Źródło | Link | Co to jest | Co bierzemy |
|---|---|---|---|
| **Bloomberg Cities Idea Exchange** | [pomysły](https://citiesideaexchange.bloomberg.org/the-ideas/) · [opis](https://www.smartcitiesdive.com/news/bloomberg-philanthropies-cities-idea-exchange-evidence-based-city-policies/729974/) | Katalog sprawdzonych rozwiązań miejskich z dowodami i instrukcją wdrożenia. 1079 miast. Tylko dla urzędników. | Wzór karty. Zdanie do pitchu: „Bloomberg robi to dla burmistrzów. My robimy to dla pani Zofii.” |
| **OECD OPSI Case Study Library** | [oecd-opsi.org](https://oecd-opsi.org/case_type/opsi/) | Setki opisanych innowacji z całego świata. | Źródło kart na start (z linkiem, więc spełnia Q33). |
| **Participedia** | [participedia.net](https://participedia.net/) | Otwarta baza przypadków partycypacji. | Jak wyżej. |
| **Baza Dobrych Praktyk** (ZMP, ZGWRP, ZPP) | [dobrepraktyki.pl](https://www.dobrepraktyki.pl/) · [opis](https://zpp.pl/artykul/70-baza-dobrych-praktyk) | Ponad 400 opisów rozwiązań z polskich gmin, w stałym formacie. | **Najlepsze polskie źródło kart na start.** Mają już pola zbliżone do naszych 6. |
| **PAP Samorząd „Jak robią inni”** | [samorzad.pap.pl](https://samorzad.pap.pl/kategoria/jak-robia-inni/naprawmy-aplikacja-naprawmytopl-w-katowicach-mieszkancy-zglaszaja-miasto) | Artykuły o rozwiązaniach w polskich miastach. | Źródło kart z linkiem. |
| **Kraków: zrealizowane Inicjatywy lokalne** | [2023](https://obywatelski.krakow.pl/281820,artykul,zrealizowane_projekty_-_2023.html) · [2022](https://obywatelski.krakow.pl/260772,artykul,zrealizowane-projekty---2022.html) | Lista: nazwa + dzielnica (np. „Skwer kieszonkowy”, Mistrzejowice; „Ogród dla społeczności lokalnej”, Krowodrza). **Bez kosztów i opisów.** | Krakowskie karty na start. Brak kosztów to argument dla nas: miasto nie zapisuje wiedzy, my tak (H1). |
| **innowacjespoleczne.pl** (Stocznia + FISE) | [profile](https://innowacjespoleczne.pl/profile/) | Katalog inkubatorów i organizacji wspierających innowacje społeczne. | Kontakty, nie karty. |

## 5. Ludzie gotowi działać i pieniądze (wzór dla Organizacji i Inicjatyw)

| Platforma | Link | Co robi | Co bierzemy |
|---|---|---|---|
| **ioby** (USA) | [o ioby](https://ioby.org/resources/civic-crowdfunding-for-trust-and-resilience/) | Mieszkańcy-liderzy zbierają pieniądze, wolontariuszy i sprzęt na projekty sąsiedzkie. 3700 projektów. | Inicjatywa potrzebuje nie tylko pieniędzy: też ludzi i rzeczy. Pomysł do pitchu: lista „czego brakuje” przy Inicjatywie. |
| **Spacehive** (UK) | [spacehive.com](https://www.spacehive.com/about) · [przykład rady](https://www.havering.gov.uk/news/article/1749/council-launches-new-spacehive-crowdfunding-scheme-to-support-community-led-projects) | Zbiórki na projekty publiczne. **Rada dopłaca** (np. do 40% celu). 90% projektów dochodzi do celu. | Pomysł na Poziom 3: miasto „dokłada” do Inicjatyw z wieloma Poparciami. Tak samo działa Inicjatywa lokalna (miasto daje materiały, mieszkańcy pracę). |
| **Neighbourly** (UK) | [neighbourly.com](https://www.neighbourly.com/) | Łączy 30 tys. małych organizacji z firmami (wolontariat pracowniczy, nadwyżki, granty). | Pomysł na drugi strumień przychodu: firmy z Krakowa sponsorują Inicjatywy w ramach CSR. |
| **Warszawa „Sąsiedzka”** | [um.warszawa.pl/waw/sasiedzka](https://um.warszawa.pl/waw/sasiedzka/inicjatywa) | Strona miasta o Inicjatywie lokalnej: 5 kroków, koordynatorzy w dzielnicach, przykłady. Formularz do pobrania. | **Wzór dla Szkicu wniosku:** 5 kroków + kryteria oceny (lokalność, zaangażowanie mieszkańców, przygotowanie). Prompt powinien pisać pod te kryteria. |
| Ochotnicy Warszawscy | [wolontariat.waw.pl](https://wolontariat.waw.pl/) | Miejski portal ofert wolontariatu. | Kontekst: miasta same łączą wolontariuszy z NGO, ale bez powiązania z Potrzebami. |

## 6. Inne zespoły z hackathonów (żeby nie powtórzyć cudzego pomysłu)

| Projekt | Link | Uwaga |
|---|---|---|
| CivicSolve (Smart India Hackathon) | [GitHub](https://github.com/Prajan77v/CivicSolve) | AI klasyfikuje problem, łączy z uczelniami i NGO, „ponowne użycie rozwiązań”. Najbliższy nam pomysł. Nie ma Inicjatywy lokalnej ani zaufania z potwierdzeń. |
| CivicResolve / CivicX (SIH 2026) | [GitHub 1](https://github.com/saaisree23/civicresolve) · [GitHub 2](https://github.com/ArchitNadiger/Team-Tech) | Podobnie: zgłoszenie → AI → eksperci. Wniosek: „AI łączy problem z pomocnikami” już się pojawia. Nasza przewaga to pętla do Sprawdzonego rozwiązania i prawdziwa procedura miasta. |

## Pomysły do rozważenia (nic z tego nie jest jeszcze decyzją)

1. **Promień podobnych zależny od Kategorii** (FixMyStreet). Mała zmiana w Q30. Gabriel.
2. **Cytaty pod Podsumowaniem dyskusji** (Talk to the City). Tomasz.
3. **Szkic wniosku pisany pod kryteria oceny miasta** (Warszawa „Sąsiedzka”). Tomasz.
4. **Karty na start z dobrepraktyki.pl + listy krakowskich Inicjatyw lokalnych.** Tomasz + Gabriel.
5. **Pitch: Hoplr i Go Vocal jako dowód, że miasta płacą.** Eryk.
6. **Pitch: Kraków ma 22 Inicjatywy lokalne rocznie. My chcemy to zwiększyć.** Eryk. Sprawdzić rok tej liczby na [krakow.pl](https://www.krakow.pl/aktualnosci/278957,26,komunikat,zglos_projekt_w_ramach_inicjatywy_lokalnej.html) przed pitchem.

## Czego nie udało się sprawdzić

- **Kim jest HubMI.pl.** Strona zadań HackYeah ładuje się dynamicznie, a wyszukiwarka nic nie zwraca. Eryk pyta na stoisku.
- Pełnej treści kart Bloomberga (strona blokuje zwykłe pobieranie). Widać tylko tytuły.
