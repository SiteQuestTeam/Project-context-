Oto ustrukturyzowana mapa procesu w aplikacji, przedstawiona w przystępny i bezpośredni sposób bez zbędnych założeń technologicznych czy kodu. Proces opisuje krok po kroku ścieżkę użytkownika od podglądu mapy do publikacji inicjatywy.

---

###  Architektura Procesu Zgłaszania Inicjatywy (Krok po Kroku)

```
[1. Podgląd Mapy i Lokalizacja] 
              
             
[2. Wybór Typu Inicjatywy: Zwiad / Misja / Rajd]
               
               
[3. Tryb Aparatu i Telemetria (Zdjęcie + GPS)]
               
               
[4. Rozmowa z Chatbotem AI (Wyciąganie intencji)]
               
               
[5. Plan Działania i Wymagane Wsparcia (Dopasowanie NGO/Urzędu)]
               
               
[6. Dobre Praktyki (Wzorce z innych miast) i Akceptacja]
               
               
[7. Zapis i Publikacja Nowej Pinezki na Mapie]

```

---

### Detailed Step Breakdown

#### 1. Live Map & Tracking (Lokalizacja Gracza)

* **Widok:** Interaktywna mapa z widoczną postacią/awatarem użytkownika.
* **Działanie:** Pozycja awatara aktualizuje się na żywo wraz z fizycznym przemieszczaniem się mieszkańca w terenie.
* **Promień Interakcji:** Wokół awatara wyznaczony jest obszar interakcji (promień 50m) pozwalający na podejmowanie akcji w najbliższym otoczeniu.

#### 2. Wybór Typu Inicjatywy

Gdy użytkownik klika przycisk dodania akcji, wybiera jedną z 3 kategorii zgłoszenia:

* ** Zwiad (Pasywne zgłoszenie):**
* *Zasada:* Wskazanie problemu bez bezpośredniej fizycznej ingerencji zgłaszającego (naprawia ktoś inny / urząd).
* *Efekt:* Bez zmiany miejsca.
* *Przykład:* Zgłoszenie braku stojaka na rowery przy miejscu, gdzie ludzie przypinają je do rury.


* ** Misja (Pomoc społeczna / Relacyjna):**
* *Zasada:* Pomoc ludziom lub okolicy bez wprowadzania trwałej zmiany w infrastrukturze miejsca. Wybór trybu **SOLO** lub **W GRUPIE**.
* *Przykład:* Solo (pomoc sąsiadce w wniesieniu zakupów) lub W Grupie (pomoc seniorom w obsłudze telefonów w bibliotece).


* ** Rajd (Przekształcenie przestrzeni):**
* *Zasada:* Akcja ukierunkowana na trwałą zmianę fizyczną danego miejsca (np. zmiana "Szarego Miejsca" w przestrzeń zieloną). Zawsze odbywa się **W GRUPIE** z ustalonym miejscem i czasem.
* *Przykład:* Sąsiedzkie sprzątanie i urządzanie zaniedbanego skweru.



#### 3. Tryb Przechwytywania Zdjęcia i Telemetrii

* **Wymuszone zdjęcie na żywo:** Aplikacja uruchamia aparat w trybie robienia zdjęcia w danym momencie (blokada wyboru gotowych plików z galerii telefonu).
* **Automatyczne pobranie danych:** Podczas wykonywania zdjęcia system przechwytuje dokładną pozycję GPS, kierunek kompasu oraz znacznik czasu.
* **Ochrona prywatności (RODO):** Skrypt po stronie telefonu automatycznie nakłada rozmycie na wykryte twarze oraz tablice rejestracyjne.

#### 4. Analiza Wizyjna i Rozmowa z Chatbotem AI

* Użytkownik zatwierdza wykonane zdjęcie.
* Model AI (Bóbr Borys) analizuje obraz, odczytując kontekst miejsca oraz wykryty problem.
* Chatbot otwiera okno rozmowy i dopytuje użytkownika o szczegóły: co dokładnie chciałby zmienić, jakie ma intencje oraz jakich konkretnie środków lub pomocy potrzebuje.

#### 5. Plan Działania i Dopasowanie Podmiotów

* **Wymogi akcji:** AI podsumowuje ustalenia z rozmowy i tworzy checklistę wymagań niezbędnych do realizacji inicjatywy (np. podział ról: potrzebny sprzęt, transport, praca fizyczna).
* **Dopasowanie instytucji:** System automatycznie odpytuje bazę danych o właściwe jednostki miejskie (np. ZZM, ZDM) oraz pobliskie organizacje pozarządowe (NGO z KRS API), które odpowiadają za dany obszar lub podejmują pokrewne działania.

#### 6. Dobre Praktyki i Ostateczna Akceptacja

* **Karty Wzorcowe:** AI prezentuje użytkownikowi 1–2 sprawdzone rozwiązania z innych miast lub dzielnic, pokazując jak podobny problem został pomyślnie rozwiązany w przeszłości.
* **Zatwierdzenie:** Użytkownik przegląda wygenerowany podsumowujący opis inicjatywy, nanosi ewentualne poprawki i daje ostateczną akceptację.

#### 7. Zapis i Publikacja na Mapie

* **Geo-Deduplikacja:** Przed dodaniem nowej pinezki system sprawdza promień 20 metrów od podanych współrzędnych. Jeśli w tym miejscu istnieje już analogiczna inicjatywa, zamiast nowej pinezki podbijany jest licznik wsparcia istniejącego wpisu.
* **Render nowej pinezki:** Jeśli w okolicy nie ma duplikatu, na mapie wszystkich aktywnych użytkowników pojawia się nowa świecąca pinezka/pylon symbolizujący utworzoną inicjatywę.