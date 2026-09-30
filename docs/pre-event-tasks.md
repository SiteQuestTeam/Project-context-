# Zadania przed hackathonem (1–2 października)

Hackathon startuje 3 października o 10:00, zadania odblokowują się o 11:00.
Tu jest tylko praca, którą warto zrobić **przed**: badania, dane, testy narzędzi.
Właściwy kod aplikacji piszemy na miejscu.
Pojęcia pisane wielką literą są zdefiniowane w [CONTEXT.md](../CONTEXT.md).

## Kacper + Gabriel

- [ ] **Test EgoBlur** ([ADR 0005](adr/0005-blur-before-any-ai-sees-a-photo.md)).
  Pobrać modele ze strony Project Aria, uruchomić `pip install egoblur` na Linuxie (albo Docker/WSL),
  sprawdzić na 5 zdjęciach ulic z twarzami i tablicami.
  Jeśli nie działa po godzinie: zapasowo `deface` (tylko twarze).

## Tomasz

- [ ] **Test modeli AI** (Q27). 15 zdjęć + opisów Potrzeb po polsku (rozmytych!).
  Dać je Gemini Flash i Claude Haiku 4.5, porównać trafność Kategorii i Poziomu zagrożenia.
  Sprawdzić też Szkic wniosku na Claude Sonnet 5.5. Wybrać model.
- [ ] **Lista Sprawdzonych rozwiązań** razem z Erykiem (Q7), ok. 20–30 przypadków.
- [ ] Przygotować się do **Szkicu wniosku o Inicjatywę lokalną** (Q16): pobrać wzór wniosku z krakow.pl,
  zobaczyć, jakie pola ma.

## Eryk

- [ ] **Tabela Kategoria → Jednostka miejska** (Q29), ok. 10 wierszy.
  Kto w Krakowie odpowiada za: drogi i chodniki, latarnie, zieleń i ławki, śmieci, wodę, graffiti, place zabaw…
  Dla każdej: nazwa, jak się z nią kontaktować, źródło.
- [ ] **Lista Sprawdzonych rozwiązań** razem z Tomaszem (Q7). Każda karta: problem, co zrobiono, gdzie, kto, koszt i czas, **źródło (link, obowiązkowe)**.
- [ ] **Nazwa** (Q37): robocza „Sąsiedzisko”. Sprawdzić, czy nazwa i domena `.pl` są wolne; zaproponować ostateczną.
- [ ] **Model biznesowy do pitchu** (Q38): pilotaż za grant → abonament miasta / rad dzielnic.

## Wszyscy

- [ ] **5 zdjęć prawdziwych problemów** na osobę (Q44): dziura, zepsuta ławka, graffiti, brak rampy, przepełniony kosz…
  Najlepiej w czwartek albo piątek, w dowolnym mieście; ewentualnie już w Krakowie. Razem 30 zdjęć do przykładowych Potrzeb.
  Bez zdjęć z internetu (licencje). Zdjęcia i tak przejdą przez rozmycie.

## Do przydzielenia

- [ ] **Lista ok. 50 Organizacji** z Grzegórzek i okolic z [ngo.krakow.pl](https://ngo.krakow.pl) (Q8).
  Zbierać ręcznie, bez robota ściągającego całą stronę. Z numerem KRS, jeśli jest.
- [ ] **Konto w Claude Console** z doładowaniem ok. $5–10, jeśli test wybierze Claude.
  Klucz tylko w `.env`, nigdy w repozytorium (repozytorium będzie publiczne).
