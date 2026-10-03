# SideQuest — MVP (plan na drugą połowę hackathonu)

Ustalone w grillu 3.10 wieczorem. Pojęcia: [CONTEXT.md](CONTEXT.md). Dlaczego tak: [ADR 0010](docs/adr/0010-mvp-initiatives-with-ai-brief.md).
Ten plik jest wersją po uzgodnieniach z Erykiem. Tam, gdzie różni się od [Rozmowa z Erykiem.md](Rozmowa%20z%20Erykiem.md) (SWOT, przykłady z innych miast, Głos do 50 m, nazwa „Punkty”), obowiązuje ten plik.
Stary kontekst (BRIEF v3, ADR 0001–0009) jest w gałęzi `archiwizowane`. Gra (Zwiad, Misja, Rajd, Odbicia, Weryfikatorzy, Liga dzielnic) wraca dopiero, gdy MVP działa.

Najpierw dowozimy 4 rzeczy, potem je upiększamy.

---

## 🎯 Cel: 4 funkcjonalności

1. **Mapa z Awatarem.** Awatar stoi w prawdziwej pozycji GPS Gracza. Na mapie są pinezki Inicjatyw.
2. **Zgłoszenie Inicjatywy z AI.** Zdjęcie na żywo na miejscu → Claude zadaje max 3 pytania → krótki **Brief** → Gracz poprawia i zatwierdza → nowa pinezka.
3. **Głos.** Tylko na miejscu (do ok. 50 m od Inicjatywy), jeden Głos na Gracza na Inicjatywę. Przy **Progu** (10 Głosów) Inicjatywa „Przeszła”.
4. **Punkty i Nagrody** + landing page i logo. Punkty wydaje się na Nagrody od Sponsorów.

## Zasady, których się trzymamy

- **Nie da się zagłosować z kanapy.** Głos i zgłoszenie tylko na miejscu (GPS ok. 50 m).
- **Zdjęcie na żywo:** tylko aparat w aplikacji, bez galerii.
- **Punkty:** dużo za zgłoszenie Inicjatywy, mało za Głos. Gdy Inicjatywa przechodzi, premię dostają Inicjator i wszyscy, którzy na nią głosowali. Liczby ustala zespół psychologiczny.
- **Ranga** liczy wszystkie Punkty zdobyte kiedykolwiek. Wydanie Punktów jej nie obniża.
- **Wszystkie Punkty liczy serwer,** nigdy telefon.
- **Logowanie:** tylko pseudonim, bez hasła. W pitchu: w pełnej wersji mObywatel.
- **Klucz API Claude tylko na serwerze** (w `.env`). Repo jest publiczne.

---

## 📋 Zadania

### 🗺️ Strumień 1: Aplikacja (mapa i ekrany)

- [ ] **1.1 Mapa i Awatar:** mapa na cały ekran, Awatar w pozycji GPS, okrąg ok. 50 m wokół Awatara.
- [ ] **1.2 Pinezki Inicjatyw:** pobranie listy, pinezka w kolorze statusu („Zbiera głosy” / „Przeszła”), podgląd Inicjatywy (Brief + licznik `9/10`).
- [ ] **1.3 Głos:** przycisk `[ Oddaj Głos ]` aktywny tylko w promieniu 50 m. Licznik rośnie, Punkty dochodzą do salda.
- [ ] **1.4 Zgłoszenie:** aparat (bez galerii) → okno rozmowy z AI (max 3 pytania) → ekran Briefu do poprawy i zatwierdzenia.
- [ ] **1.5 Portfel i Nagrody:** saldo Punktów, Ranga, lista Nagród od Sponsorów z ceną w Punktach, przycisk „Odbierz”.

### 🧠 Strumień 2: Backend i AI

- [ ] **2.1 Dane i API:** `Inicjatywy` (id, Inicjator, lat, lng, zdjęcie, Brief, liczba Głosów, status), `Głosy` (Gracz, Inicjatywa — jeden na parę), `Gracze` (pseudonim, saldo, suma Punktów do Rangi), `Nagrody`.
- [ ] **2.2 Zasady na serwerze:** sprawdzenie 50 m przy Głosie i zgłoszeniu, jeden Głos na Gracza, Próg 10 → status „Przeszła” + premia, wydawanie Punktów na Nagrody.
- [ ] **2.3 Endpoint AI:** zdjęcie + odpowiedzi Gracza → Claude **Sonnet 5.5** → Brief jako JSON. **Awaria:** po ok. 8 s serwer oddaje gotowy Brief dla zdjęcia z demo. (Wpina Patryk.)
- [ ] **2.4 „Mózg AI”:** prompt systemowy, `schema.json` Briefu, przykłady rozmów, test na 10–20 zdjęciach. (Tomasz.) Badanie formularzy: [docs/research-ai-form.md](docs/research-ai-form.md).
- [ ] **2.5 Dane przykładowe:** 3–4 Inicjatywy w Krakowie z gotowymi Briefami + **„Stoisko z gorącą herbatą na HackYeah 2026” przy Tauron Arenie z 9/10 Głosami** + 3 Sponsorzy z Nagrodami.

**Brief ma 9 pól:** tytuł (do 60 znaków), kategoria, problem, proponowane działanie, dlaczego to ważne, potrzebne zasoby (ludzie, sprzęt, transport), Kto naprawi (Miasto / Gildia / Gracze: 2 pytania tak/nie, AI podpowiada, Gracz potwierdza), miejsce i zdjęcie (z telefonu).
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
- Logowanie przez mObywatel. Punkty dopiero po weryfikacji (ochrona przed oszustwem).

## Wskazówki na teraz

- **Mocki tam, gdzie się da.** 1–2 świetne przykłady na sztywno, które na pewno zadziałają na pitchu.
- **Najpierw cała ścieżka demo, potem upiększanie.**
