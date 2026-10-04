# SideQuest — MVP (plan na drugą połowę hackathonu)

Ustalone w grillu 3.10 wieczorem. Część o AI (Usterka i Inicjatywa, pytania, Brief) poprawiona po grillu 3–4.10: szczegóły w [ai/](ai/README.md). Pojęcia: [CONTEXT.md](CONTEXT.md). Dlaczego tak: [ADR 0010](docs/adr/0010-mvp-initiatives-with-ai-brief.md).
Ten plik jest wersją po uzgodnieniach z Erykiem. Tam, gdzie różni się od [Rozmowa z Erykiem.md](Rozmowa%20z%20Erykiem.md) (SWOT, przykłady z innych miast, Głos do 50 m, nazwa „Punkty”), obowiązuje ten plik.
Stary kontekst (BRIEF v3, ADR 0001–0009) jest w gałęzi `archiwizowane`. Gra (Zwiad, Misja, Rajd, Odbicia, Weryfikatorzy, Liga dzielnic) wraca dopiero, gdy MVP działa.

Najpierw dowozimy 4 rzeczy, potem je upiększamy.

---

## 🎯 Cel: 4 funkcjonalności

1. **Mapa z Awatarem.** Awatar stoi w prawdziwej pozycji GPS Gracza. Na mapie są pinezki Inicjatyw i Usterek.
2. **Zgłoszenie z AI.** Zdjęcie na żywo na miejscu → AI rozpoznaje **Usterkę** (trzeba naprawić) albo **Inicjatywę** (zmiana, nad którą się głosuje) → przy Inicjatywie 2 pytania → krótki **Brief** → Gracz poprawia i zatwierdza → nowa pinezka. Usterkę aplikacja wysyła do KCK dopiero po kliknięciu `[ Wyślij do KCK ]` (zadanie 1.6).
3. **Głos.** Tylko na miejscu (do ok. 50 m od Inicjatywy), jeden Głos na Gracza na Inicjatywę. Przy **Progu** (10 Głosów) Inicjatywa „Przeszła”.
4. **Punkty i Nagrody** + landing page i logo. Punkty wydaje się na Nagrody od Sponsorów.

## Zasady, których się trzymamy

- **Nie da się zagłosować z kanapy.** Głos i zgłoszenie tylko na miejscu (GPS ok. 50 m).
- **Zdjęcie na żywo:** tylko aparat w aplikacji, bez galerii. Nowe zdjęcie, gdy twarz jest głównym tematem albo widać czytelną tablicę rejestracyjną. Przechodnie w tle są w porządku (art. 81 prawa autorskiego).
- **Tylko miejsca publiczne.** Nie na prywatnej posesji. Podwórko osiedla albo parafii jest w porządku.
- **Możliwe zagrożenie:** AI pokazuje ostrzeżenie (co wykryło) i pyta, czy to prawda. Tak: „odejdź, nie dotykaj, ostrzeż ludzi”, przyciski `112` i (przy prądzie) `991`, koniec zgłoszenia, **zero Punktów**, żeby nikt nie podchodził do zagrożenia dla nagrody. Nie: zgłoszenie idzie dalej, bo AI może się pomylić. Przewrócony słup to zawsze zagrożenie.
- **Punkty:** dużo za zgłoszenie Inicjatywy, coś za Usterkę przyjętą przez KCK, mało za Głos i za Zainteresowanie (zgłoszenie czegoś, co już jest na mapie; nie idzie do KCK). Gdy Inicjatywa przechodzi, premię dostają Inicjator i wszyscy, którzy na nią głosowali. Liczby ustala zespół psychologiczny.
- **Ranga** liczy wszystkie Punkty zdobyte kiedykolwiek. Wydanie Punktów jej nie obniża.
- **Wszystkie Punkty liczy serwer,** nigdy telefon. Za Usterkę Punkty są naliczane dokładnie raz dopiero po tym, gdy KCK przyjmie zgłoszenie i zwróci `incidentId`; przygotowanie szkicu, błąd lub niepotwierdzony timeout nie daje Punktów.
- **Logowanie:** tylko pseudonim, bez hasła. W pitchu: w pełnej wersji mObywatel.
- **Klucz API OpenAI tylko na serwerze** (w `.env`). Repo jest publiczne.
- **Usterki miejskie są osobną ścieżką od Inicjatyw.** Typowe usterki (np. dziura, uszkodzony chodnik, zanieczyszczenie, problem z zielenią lub zwierzętami) wysyłamy wyłącznie do Krakowskiego Centrum Kontaktu. Gracz nie wybiera wydziału ani „Kto naprawi”. Szczegóły: [docs/kck-integration.md](docs/kck-integration.md).

---

## 📋 Zadania

### 🗺️ Strumień 1: Aplikacja (mapa i ekrany)

- [ ] **1.1 Mapa i Awatar:** mapa na cały ekran, Awatar w pozycji GPS, okrąg ok. 50 m wokół Awatara. Na mapie są tylko Inicjatywy. Usterek nie ma na mapie, bo nikt na nie nie głosuje.
- [ ] **1.2 Pinezki:** pobranie listy, pinezka w kolorze statusu (Inicjatywa: „Zbiera głosy” / „Przeszła”), podgląd (Brief + licznik `9/10` przy Inicjatywie).
- [ ] **1.3 Głos:** przycisk `[ Oddaj Głos ]` aktywny tylko w promieniu 50 m. Licznik rośnie, Punkty dochodzą do salda.
- [ ] **1.4 Zgłoszenie:** aparat (bez galerii) z linią „Co chcesz zgłosić?” → swipe Usterka/Inicjatywa → przy Inicjatywie 2 pytania z podpowiedziami → ekran Briefu do poprawy i zatwierdzenia. Usterka po swipie przechodzi do ekranu z zadania 1.6. Ekrany i stałe teksty: [ai/README.md](ai/README.md), [ai/stale-teksty.md](ai/stale-teksty.md).
- [ ] **1.5 Portfel i Nagrody:** saldo Punktów, Ranga, lista Nagród od Sponsorów z ceną w Punktach, przycisk „Odbierz”.
- [ ] **1.6 Usterka → KCK:** Zdjęcie na żywo + GPS → automatyczne przygotowanie kategorii, tytułu, opisu i adresu → ekran podglądu/edycji → `[ Wyślij do KCK ]` → pokazanie numeru zgłoszenia.

### 🧠 Strumień 2: Backend i AI

- [ ] **2.1 Dane i API:** `Inicjatywy` (id, Inicjator, lat, lng, zdjęcie, jeden ostateczny Brief zatwierdzony przez Gracza, liczba Głosów, status), `Usterki` (`CityIncident` z [docs/kck-integration.md](docs/kck-integration.md)), `Zainteresowania` (Gracz, Usterka albo Inicjatywa — jedno na parę), `Głosy` (Gracz, Inicjatywa — jeden na parę), `Gracze` (pseudonim, saldo, suma Punktów do Rangi), `Nagrody`.
- [ ] **2.2 Zasady na serwerze:** sprawdzenie 50 m przy Głosie i zgłoszeniu, jeden Głos na Gracza, Próg 10 → status „Przeszła” + premia, wydawanie Punktów na Nagrody.
- [ ] **2.3 Endpoint AI:** dwa kroki z OpenAI **gpt-6.1-sol**, `effort: low` (Patryk ma opłacone API OpenAI; ok. $0.03–0.06 za zgłoszenie): (1) zdjęcie → zagrożenie, kontrola zdjęcia, typ i pytania, (2) Inicjatywa: odpowiedzi → Brief jako JSON; Usterka: osobny prompt KCK, jedno wywołanie → pola KCK albo `RETAKE`. Każde wywołanie: `store: false`, timeout 8 s (pisanie Briefu: 15 s, bo trwa ok. 8 s), bez ponowień. Kod: Backend, gałąź `feat/final-backend` (repo backend-ai jest zamrożone); dla `POST /kck/prepare` jest funkcja `przygotujUsterkeKck`. Adres z GPS przez miejską usługę MSIP, tak jak w KCK (`AddressService`). **Awaria:** po przekroczeniu limitu aplikacja pokazuje Bobra z komunikatem „Przepraszamy, spróbuj później”.
- [ ] **2.4 „Mózg AI”:** [ai/](ai/README.md): 2 prompty systemowe, 2 schematy JSON, przykłady, test na 10–20 zdjęciach. (Tomasz.) Badanie formularzy: [docs/research-ai-form.md](docs/research-ai-form.md).
- [ ] **2.5 Dane przykładowe:** 3–4 Inicjatywy w Krakowie z gotowymi Briefami + **„Stoisko z gorącą herbatą na HackYeah 2026” przy Tauron Arenie z 9/10 Głosami** + 3 Sponsorzy z Nagrodami.
- [ ] **2.6 Integracja KCK:** `POST /kck/prepare` i `POST /kck/submit`, klasyfikacja do 5 kategorii KCK, GPS → adres, anonimowy `multipart/form-data` do KCK (`dto` + `file`), zapis i zwrot `incidentId`; dopiero po potwierdzonym `incidentId` backend nalicza Graczowi Punkty za Usterkę, dokładnie raz. Implementacja według [docs/kck-integration.md](docs/kck-integration.md).

**Brief Inicjatywy ma 9 pól:** tytuł (do 60 znaków), kategoria (Budżetu Obywatelskiego), problem, proponowane działanie, dlaczego to ważne, potrzebne zasoby (ludzie, sprzęt, transport), Kto naprawi (Miasto / Gracze: 1 pytanie tak/nie, AI podpowiada, Gracz potwierdza), miejsce i zdjęcie (z telefonu).
**Usterka nie ma Briefu, tylko pola KCK:** kategoria (`DAMAGE`, `POLLUTION`, `GREENERY`, `ANIMALS`, `OTHER`), tytuł `summary` (do 60 znaków), opis `description` (do 500), adres z GPS i zdjęcie. AI nie zadaje pytań.
**Bez SWOT i bez wzorców z innych miast:** AI łatwo je wymyśla, a jury zapyta o źródło. Te rzeczy są tylko w pitchu.

### 🎨 Strumień 3: Design, landing page i pitch

- [ ] **3.1 Logo i 3 kolory** wspólne dla aplikacji i landing page'a. Styl prosty, przejrzysty, „applowski”.
- [ ] **3.2 Landing page:** nagłówek, logo, przycisk `[ Uruchom aplikację ]`. Sekcje: Czym jest SideQuest? · Jak to działa (Zdjęcie na miejscu → Brief z AI → Głosy → Punkty i Nagrody) · Sponsorzy.
- [ ] **3.3 Zabawna Nagroda na demo** (zespół psychologiczny).
- [ ] **3.4 Pitch (PDF max 10 slajdów) i scenariusz demo.**

---

## 🎬 Demo

1. Pokazujemy mapę z Awatarem i pinezkami.
2. Zgłaszamy Inicjatywę na żywo: zdjęcie → AI dopytuje → Brief → pinezka.
3. Pinezka „Stoisko z gorącą herbatą na HackYeah 2026” ma **9/10 Głosów**. Jury oddaje Głos przy Tauron Arenie → **10/10, „Przeszła”**.
4. Opowiadamy, jak projekt zostaje zrealizowany. Jury dostaje Punkty i wydaje je na zabawną Nagrodę.

## Tylko w pitchu (po MVP)

- Próg różny dla każdej Inicjatywy.
- Zrealizowane Inicjatywy na profilu Gracza.
- Wzorce z innych miast, dopasowanie NGO (KRS) i urzędów.
- Gra: Zwiady, Misje, Rajdy, Odbicia, Weryfikatorzy, Liga dzielnic, Odznaki.
- Logowanie przez mObywatel. Punkty dopiero po weryfikacji (ochrona przed oszustwem). Zgłaszają tylko mieszkańcy.
- Gildia jako trzecia odpowiedź Kto naprawi.
- Znacznik „niebezpieczne miejsce” na mapie po potwierdzonym zagrożeniu, żeby ostrzec innych.
- Teren prywatny sprawdzany po GPS na miejskiej mapie działek.
- Status „Wykonane” po zdjęciu „po naprawie”. Takie przypadki uczą AI (lepsze przykłady w promptach).

## Wskazówki na teraz

- **Mocki tam, gdzie się da.** 1–2 świetne przykłady na sztywno, które na pewno zadziałają na pitchu.
- **Najpierw cała ścieżka demo, potem upiększanie.**
