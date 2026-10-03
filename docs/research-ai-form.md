# Research: the form the AI fills after Scouting

Date: 2026-10-03. The question: what should the short form contain that an AI (Claude with vision) fills from a Live photo plus at most 2 follow-up questions? We will prompt an existing model, not train one, so the form has to rest on real fields.

Vocabulary follows `CONTEXT.md` (Player, Scouting, Grey spot, Who fixes, Guild, Reviewer). Polish sources are summarised in Polish.

---

## 1. Real forms and their fields

### 1a. Kraków: wniosek o realizację inicjatywy lokalnej (art. 19b ustawy o działalności pożytku publicznego)

**Źródło:** procedura [BIP Kraków DK-1](https://www.bip.krakow.pl/uslugi/DK-1). Formularz pobrany z [kontakt.krakow.pl (plik .docx, „Załącznik nr 1 do Zarządzenia Prezydenta Miasta Krakowa”)](https://kontakt.krakow.pl/c/document_library/get_file?uuid=f6f1860d-d83f-dd3d-7e46-7931c56818fa&groupId=536063) i przeczytany w całości. Podstawa prawna wymieniona w formularzu: [uchwała Nr LXXXI/1969/2017 Rady Miasta Krakowa z 30.08.2017](https://www.bip.krakow.pl/uslugi/DK-1). Starsza [instrukcja wypełniania wniosku (2019)](https://obywatelski.krakow.pl/246599,artykul,inicjatywy.html/243936,artykul,inicjatywa_lokalna___instrukcja_wypelniania_wniosku___2019.html) traktuje wszystkie punkty jako obowiązkowe.

Formularz jest papierowy (Word), bez gwiazdek. Obowiązkowość poniżej wynika z treści formularza („jeśli dotyczy”) i z instrukcji 2019.

| # | Pole (dosłownie z formularza) | Obowiązkowe? | Uwagi |
|---|---|---|---|
| 1 | Tytuł | tak | |
| 2 | Krótki opis | tak | |
| 3 | Wnioskodawcy: A. Mieszkańcy (imię i nazwisko, adres zamieszkania) **albo** B. Organizacja pozarządowa (nazwa, siedziba, KRS, reprezentant) | tak | |
| 4 | Osoba/osoby do kontaktu (imię, nazwisko, telefon, e-mail) | tak | |
| 5 | Obszary działalności, których dotyczy inicjatywa (checkboxy, można kilka) | tak | 11 obszarów, m.in. „budowa, rozbudowa, remont dróg, budynków oraz obiektów architektury”, „ochrona przyrody, w tym zieleni miejskiej”, „porządek i bezpieczeństwo publiczne”, „rewitalizacja”, „kultura fizyczna i turystyka” |
| 6 | Opis zadania publicznego oraz stanu jego przygotowania lub realizacji | tak | przebieg, etapy, dostępność dla osób ze szczególnymi potrzebami |
| 7 | Termin realizacji | tak | nie wcześniej niż 8 tygodni od złożenia |
| 8 | Miejsce realizacji (Dzielnica/Dzielnice) + dokładne miejsce | tak | **jeśli teren nie jest we władaniu Miasta, trzeba dołączyć zgodę dysponenta terenu** |
| 9 | Znaczenie dla społeczności lokalnej: potrzeby mieszkańców; do kogo skierowana | tak | |
| 10 | Szacowane zaangażowanie wnioskodawców: praca społeczna (rodzaj, liczba osób, godziny, stawka), wkład rzeczowy, wkład finansowy | praca społeczna tak; rzeczowy i finansowy „jeśli dotyczy” | udział procentowy pracy społecznej jest punktowany |
| 11 | Szacowane zaangażowanie rzeczowe lub finansowe Gminy | tak | |
| 12 | Całkowity koszt realizacji | tak | |
| 13 | Dodatkowe informacje | nie | partnerzy, konsultacje |
| 14 | Opinia Rady Dzielnicy | nie | pozytywna opinia = +10 pkt |
| 15 | Data i podpisy | tak | |

Wymagane załączniki ([DK-1](https://www.bip.krakow.pl/uslugi/DK-1)): lista osób popierających, oświadczenie o pośrednictwie (jeśli przez NGO), deklaracja zaangażowania mieszkańców, zgoda dysponenta terenu (jeśli teren nie jest miejski).

**Wniosek dla nas:** inicjatywa lokalna to Raid z udziałem miasta, a nie zgłoszenie problemu. Ze zdjęcia AI wypełni tylko pola 1, 2, 5, 6 (szkic), 8 i 9. Koszty, termin i podpisy zostają dla ludzi.

### 1b. Kraków: Budżet Obywatelski, formularz projektu (edycja 2026)

**Źródło:** [Instrukcja składania projektu, EDYCJA 2026, wersja z 13.02.2026 (PDF, 31 stron)](https://plikimpi.krakow.pl/zalacznik/550629), linkowana z [budzet.krakow.pl](https://budzet.krakow.pl/zostan-tworca-projektu/309462,artykul,instrukcja-skladania-projektu.html). Formularz jest tylko online, wymaga konta z PESEL i weryfikacji SMS. Pola z gwiazdką (*) są obowiązkowe, ale gwiazdki są tylko na zrzutach ekranu, nie w tekście. Poniżej „tak” tam, gdzie tekst mówi „jesteśmy zobligowani” albo podaje minimum znaków.

| Krok | Pole | Obowiązkowe? | Limit / uwagi |
|---|---|---|---|
| 1 | Charakter: dzielnicowy / ogólnomiejski (+ dzielnica) | tak | ustala maksymalny budżet |
| 1 | Kategoria | tak | 9 kategorii (filtr na [budzet.krakow.pl/projekty2026](https://budzet.krakow.pl/projekty2026/)): **Zdrowie, Infrastruktura, Edukacja, Kultura, Bezpieczeństwo, Zieleń, Sport, Rowery, Społeczeństwo** |
| 1 | Tytuł propozycji zadania | tak | **maks. 60 znaków** |
| 1 | Krótki opis | tak | **60–250 znaków** |
| 1 | „Dotyczy całego obszaru” albo Miejsce realizacji (adres) + dodatkowe lokalizacje | tak | pinezka na mapie Google |
| 1 | Czy wymagana zgoda dysponenta terenu | tak (checkbox) | jeśli tak, oświadczenie jako załącznik |
| 2 | Szczegółowy opis | tak | min. 60 znaków |
| 2 | Uzasadnienie (cel i potrzeba, wpływ na mieszkańców) | tak | |
| 2 | Liczba uczestników | tak | |
| 2 | Opis procesu rekrutacji | wg instrukcji pole jest, obowiązkowość niejasna | |
| 2 | Wykaz sprzętu | nie („może, ale nie musi”) | |
| 2 | Uzasadnienie ogólnodostępności | tak | |
| 2 | Załączniki (mapki, zdjęcia) | nie | maks. 5 MB na plik |
| 3 | Kosztorys: nazwa składowej, opis, koszt | tak | |
| 3 | Harmonogram: nazwa działania, opis, data | tak | |
| 3 | Lista poparcia | tak | 15 podpisów mieszkańców dzielnicy lub miasta |
| 4 | Dodatkowy telefon | nie | |
| 4 | Zgoda na upublicznienie wizerunku | nie | |
| 4 | Plik ze zgodą dysponenta terenu | tak, jeśli zaznaczono w kroku 1 | |

Kategorie podał też [Fakty Krakowa](https://faktykrakowa.pl/20260213991240/budzet-obywatelski-krakowa-2026-54-mln-zl-na-pomysly-mieszkancow) („jednej z dziewięciu kategorii”).

**Wniosek dla nas:** limity BO są dobrymi limitami dla naszego formularza. Tytuł do 60 znaków i opis 60–250 znaków to pola, które AI napisze ze zdjęcia. Wtedy Szare miejsce da się później skopiować do BO bez przepisywania.

### 1c. Kraków: „Zgłoś problem” (Krakowskie Centrum Kontaktu, kontakt.krakow.pl / mKraków)

**Źródło:** komunikat miasta [„Krakowski Portal Usług Miejskich już działa!” (publikacja 2024-03-06, aktualizacja 2024-05-27)](https://www.krakow.pl/aktualnosci/280683,26,komunikat,krakowski_portal_uslug_miejskich_juz_dziala_.html), cytat dosłowny:

> „W celu rejestracji zgłoszenia wystarczy wpisać krótki opis zdarzenia i podać adres, w którym ono wystąpiło, ale nie tylko! Można również zaznaczyć miejsce wystąpienia problemu na interaktywnej mapie i dołączyć wykonane zdjęcia. […] Do każdego zgłoszenia zostanie przypisany numer, dzięki któremu będzie można śledzić jego status. […] Powiadomienia o statusie problemu będzie można otrzymać na numer telefonu lub adres e-mail.”

| Pole | Obowiązkowe? |
|---|---|
| Krótki opis zdarzenia | tak („wystarczy”) |
| Adres | tak („wystarczy”) |
| Pinezka na mapie | nie („można również”) |
| Zdjęcia | nie |
| Telefon lub e-mail (do powiadomień o statusie) | nie wynika jednoznacznie z tekstu; potrzebne do powiadomień |
| (nadawane przez system) numer zgłoszenia, status | n/d |

Przykłady problemów według miasta: uszkodzony chodnik, zalegające śmieci, połamane drzewa, awaria oświetlenia. Przez „Zgłoś pomysł” (`kontakt.krakow.pl/zglos-pomysl`) można też zgłosić np. nową ławkę, karmnik albo dodatkowy kosz. Liczby z [Fakty Krakowa, 2026-09-23](https://faktykrakowa.pl/20260923371524/krakowianie-zglaszaja-problemy-84-proc-konczy-sie-interwencja): 16 259 problemów i pomysłów w styczniu–sierpniu 2026; 84% zgłoszeń kończy się interwencją; prawie 60% pomysłów dotyczy organizacji ruchu, komunikacji i zieleni. Zgłoszenia przyjmuje też aplikacja mKraków.

**Ograniczenie:** samego formularza nie widać bez logowania i JavaScriptu. Strona [kontakt.krakow.pl/zglos-problem](https://kontakt.krakow.pl/zglos-problem) pokazuje publicznie tylko tekst zastępczy „Lorem ipsum” (sprawdzone w przeglądarce headless 2026-10-03). Nie mamy więc listy kategorii KCK. Jeśli istnieje, jest za logowaniem. Pola powyżej pochodzą z opisu miasta, nie z samego formularza.

**Wniosek dla nas:** miejskie zgłoszenie to w praktyce opis, adres i zdjęcie. Nasze Szare miejsce z oceną „Kto naprawi = Miasto” ma wszystko, czego potrzebuje KCK.

### 1d. Open311 GeoReport v2 (FixMyStreet, SeeClickFix, wiele miast w USA)

**Source:** [GeoReport v2 spec, wiki.open311.org](https://wiki.open311.org/GeoReport_v2/). Also [FixMyStreet's Open311 page](https://www.fixmystreet.com/open311).

**POST Service Request** (creating a report):

| Field | Required? | Notes |
|---|---|---|
| `jurisdiction_id` | only if the endpoint serves several jurisdictions | |
| `service_code` | **yes** | the category, from GET Service List |
| `lat` + `long` (WGS84) **or** `address_string` **or** `address_id` | **yes, one of them** | spec: lat/long is "near universally required" |
| `attribute[code]` | **yes, if** the service definition marks it `required` | category-specific follow-up questions |
| `description` | no | free text |
| `media_url` | no | URL of a photo |
| `email`, `device_id`, `account_id`, `first_name`, `last_name`, `phone` | no | reporter |
| `api_key` | per server | |

**GET Service List** (category list): `service_code`, `service_name`, `description`, `metadata` (true = has follow-up questions), `type` (realtime/batch/blackbox), `keywords`, `group`.

**GET Service Definition** (the follow-up questions for one category): each `attribute` has `variable`, `code`, `datatype` (string, number, datetime, text, singlevaluelist, multivaluelist), `required`, `datatype_description`, `order`, `description`, `values` (key/name).

**Service Request response** (status): `service_request_id`, `status` (open/closed), `status_notes`, `service_name`, `service_code`, `description`, `agency_responsible`, `service_notice`, `requested_datetime`, `updated_datetime`, `expected_datetime`, `address`, `address_id`, `zipcode`, `lat`, `long`, `media_url`.

**Typical categories (live data, fetched 2026-10-03):**
- San Francisco's public endpoint [`mobile311.sfgov.org/open311/v2/services.json`](https://mobile311.sfgov.org/open311/v2/services.json) lists 7 services in groups: Repair (parking and traffic sign repair; pothole and street issues; damaged public property), Cleaner streets (illegal postings), Parking and transportation (improper scooter and bike parking), General (park requests; tree maintenance). The ["Pothole and street issues" definition](https://mobile311.sfgov.org/open311/v2/services/input:Pothole%20%26%20Street%20Issues.json) has one required `singlevaluelist` follow-up, "Nature of request": bike lane faded, construction plate shifted, crosswalk faded, manhole cover off, pavement defect or pothole, lane markers, utility excavation, other.
- FixMyStreet UK's [`services.json`](https://www.fixmystreet.com/open311/v2/services.json?jurisdiction_id=fixmystreet) returns **2,569** category names, because each council defines its own (e.g. "Abandoned vehicle", "Accumulated Litter", "Bench", "1 signal light out"). The standard fixes the *shape* of a category, never the list.

**What this means for us:** Open311 already has our design. It gives a short category list, then at most a few category-specific `required` questions (`attribute`), then a free `description` and a `media_url`. Our "photo, then at most 2 questions" is the same pattern with the AI choosing the category.

### Common ground across all four

| Concept | Inicjatywa lokalna | Budżet Obywatelski | KCK „Zgłoś problem” | Open311 |
|---|---|---|---|---|
| Short name | Tytuł | Tytuł (≤60) | — | `service_name` (of category) |
| Category | Obszary działalności | Kategoria (9) | not public | `service_code` |
| Description | Krótki opis + Opis zadania | Krótki opis (60–250) + szczegółowy | Krótki opis | `description` |
| Location | Miejsce + Dzielnica | Adres + pinezka + dzielnica | Adres + pinezka | `lat`/`long`/`address_string` |
| Photo | (załącznik) | Załączniki ≤5 MB | Zdjęcia | `media_url` |
| Land owner / who acts | **zgoda dysponenta terenu** | **zgoda dysponenta terenu** | routed by the city | `agency_responsible` |
| Why it matters | Znaczenie dla społeczności | Uzasadnienie | — | — |
| Proposed fix | Opis zadania | Szczegółowy opis | (pomysł) | — |

Both Kraków project forms ask **whose land it is**. That is our "Who fixes" question 1. Land ownership cannot be seen in a photo, so the AI should suggest an answer there and the Player (or later a city land map) should confirm it.

---

## 2. Proposed schema (8 fields)

Rules behind it:
- **The AI writes only what a photo can show.** Location and time come from the phone (GPS, Live photo), never from the model.
- **Limits are copied from the real forms** (BO title ≤60, short description 60–250), so a Grey spot can be pasted into a BO or KCK form unchanged.
- **The 2 follow-up questions are the two "Who fixes" yes/no questions from BRIEF.md**, in that order. The AI pre-selects its suggested answer and the Player taps to confirm or flip it. This is BRIEF's "Poziom 2: AI podpowiada". The Player never types; the questions are buttons.
- Category keys are Polish and close to the BO categories, so the mapping stays one-to-one.

```json
{
  "title": "Brak stojaka rowerowego przy bibliotece",
  "category": "rowery",
  "description": "Przy wejściu do biblioteki nie ma stojaka. Pięć rowerów jest przypiętych do rury i barierki, częściowo blokują chodnik.",
  "proposed_action": "Postawić stojak na 5-6 rowerów przy wejściu, na płytach chodnikowych po lewej stronie.",
  "impact": "Rowerzyści nie mają gdzie zostawić roweru; rowery przy rurze zwężają przejście dla pieszych i wózków.",
  "who_fixes": {
    "value": "City",
    "q1_city_land_or_money": true,
    "q2_special_skills_or_tools": true,
    "answered_by": "player",
    "ai_confidence": "medium",
    "reason": "Chodnik przed budynkiem publicznym, najpewniej teren miasta; montaż wymaga kotwienia w nawierzchni."
  },
  "location": {
    "lat": 50.0619,
    "lng": 19.9368,
    "address": "ul. Przykładowa 1, Kraków",
    "district": "I Stare Miasto"
  },
  "photo": {
    "url": "https://.../spots/abc123.jpg",
    "taken_at": "2026-10-03T14:22:05+02:00"
  }
}
```

| Field | Filled by | Rule | Maps to |
|---|---|---|---|
| `title` | AI | ≤60 chars, Polish, names the problem, not the place | IL Tytuł · BO Tytuł · Open311 none (use in `description`) |
| `category` | AI | enum: `smieci`, `zielen`, `chodnik_droga`, `rowery`, `oswietlenie`, `mala_architektura` (ławki, kosze), `graffiti_dewastacja`, `bezpieczenstwo`, `inne` | BO Kategoria · IL Obszar · Open311 `service_code` |
| `description` | AI | 60–250 chars, only what is visible | BO Krótki opis · KCK opis · Open311 `description` |
| `proposed_action` | AI | one sentence, concrete | IL Opis zadania · BO Szczegółowy opis |
| `impact` | AI | one sentence, who is affected | IL Znaczenie dla społeczności · BO Uzasadnienie |
| `who_fixes` | AI suggests, Player confirms, Reviewer may correct | `City` if q1 yes; else `Guild` if q2 yes; else `Players` | IL/BO zgoda dysponenta · Open311 `agency_responsible` |
| `location` | phone GPS + reverse geocoding | never from the model | IL Miejsce + Dzielnica · BO adres + pinezka · KCK adres · Open311 `lat`/`long`/`address_string` |
| `photo` | app camera | Live photo only | BO załączniki · KCK zdjęcia · Open311 `media_url` |

Category mapping to BO and Open311 (SF groups as an example):

| Our `category` | BO kategoria | Inicjatywa lokalna: obszar | Open311 example |
|---|---|---|---|
| `smieci` | Zieleń / Społeczeństwo | ochrona przyrody, w tym zieleni miejskiej | Cleaner streets; FMS "Accumulated Litter" |
| `zielen` | Zieleń | ochrona przyrody, w tym zieleni miejskiej | SF "Tree maintenance", "Park requests" |
| `chodnik_droga` | Infrastruktura | budowa, remont dróg… | SF "Pothole and street issues" |
| `rowery` | Rowery | budowa, remont… obiektów architektury | SF "Improper scooter and bike parking" |
| `oswietlenie` | Infrastruktura / Bezpieczeństwo | porządek i bezpieczeństwo publiczne | FMS "All out - three or more street lights in a row" |
| `mala_architektura` | Infrastruktura | budowa, remont… obiektów architektury | SF "Damaged public property"; FMS "Bench" |
| `graffiti_dewastacja` | Bezpieczeństwo | porządek i bezpieczeństwo publiczne / rewitalizacja | SF "Illegal postings" |
| `bezpieczenstwo` | Bezpieczeństwo | porządek i bezpieczeństwo publiczne | — |
| `inne` | — | — | `other` |

Prompt notes (for whoever writes the call):
- Ask for the JSON through the API's structured output or a tool with a JSON schema, with `category` and `who_fixes.value` as enums, so the app never parses free text.
- Send the photo plus the reverse-geocoded address and district. The address helps the ownership guess (e.g. a housing cooperative estate vs. a city street).
- Tell the model what it **cannot** know from a photo: who owns the land, how long the problem has existed, how many people it affects. It should set `ai_confidence: "low"` there instead of guessing with confidence.
- If the photo shows no public-space problem (a selfie, an indoor shot), return `category: "inne"` with low confidence and let a Reviewer decide. Do not refuse in the UI.

---

## 3. Ready-made models, datasets and projects

| Name | What it is | Helps us in 15 h? |
|---|---|---|
| [Urban Civic Issues Image Dataset (QR4Change), Mendeley Data](https://data.mendeley.com/datasets/zndzygc3p3/2) | 4,937 photos from Pune, India: pothole/no-pothole and garbage/no-garbage; CC BY 4.0; 2025 | **No.** Only two binary classes and Indian roads. At most a handful of test photos for our prompt. |
| Urban Visual Pollution Dataset (UVPD, Kaggle, [described in Sci. Rep. 2025](https://www.nature.com/articles/s41598-025-17200-0)) and the [Data in Brief road dataset on Mendeley](https://data.mendeley.com/datasets/bb7b8vtwry) ([paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC10448253/)); similar: [Road Issues Detection Dataset, Kaggle](https://www.kaggle.com/datasets/programmerrdai/road-issues-detection-dataset) | Saudi street images. UVPD: 9,966 images, 11 classes incl. graffiti, garbage, potholes, broken signage, bad streetlight. The Data in Brief set: 34,460 images, 3 classes (excavation barriers, potholes, dilapidated sidewalks), CC BY 4.0. Road Issues: 9,660 images. | **No.** Training a detector takes longer than our whole budget, and the classes do not include "who fixes". Good as a category checklist only. |
| [TACO – Trash Annotations in Context](https://github.com/pedropro/TACO) | Litter photos "in the wild" with COCO segmentations; MIT | **No.** Detects pieces of litter. We only need "is there litter", which a vision LLM already answers. |
| [civic_issue_dataset (WWW 2019)](https://github.com/Sshanu/civic_issue_dataset) ([paper, arXiv 1901.10124](https://arxiv.org/pdf/1901.10124)) | COCO boxes for garbage, cracks, potholes, roads; MIT | **No.** Research code from 2019, Google Drive images. |
| [civic-complaint-ai (GitHub)](https://github.com/kagithaladurgaprasad-lab/civic-complaint-ai) | Demo app: photo + text + GPS → category, department, urgency, duplicate check; CLIP + Gemini + Qdrant | **Partly.** 0 stars, no licence ("educational/portfolio"), so we cannot copy code. Its output schema (category, department, urgency, duplicate) confirms the shape of ours. |

Background research, also not directly usable:
- A 2025 PRISMA review of 32 studies, ["Towards General Urban Monitoring with Vision-Language Models"](https://arxiv.org/abs/2510.12400), treats zero-shot use of general vision-language models as the main path for urban monitoring.
- [Vrabie 2025, "Improving municipal responsiveness through AI-powered image analysis in E-Government"](https://arxiv.org/abs/2504.08972) used citizen-submitted photos from a Romanian municipality; the abstract gives no metrics.
- The [Scientific Reports 2025 "zero-shot LLM framework for multimodal grievance classification"](https://www.nature.com/articles/s41598-025-32079-7) is about text and voice, not photos.
- mySociety (FixMyStreet's maker) added [photo-first reporting](https://www.mysociety.org/category/community/fixmystreet/) that reads GPS from the photo, and writes about [checking LLM output in stages](https://www.mysociety.org/category/ai/). Their [2017 "AI" experiment](https://www.mysociety.org/2017/07/24/training-an-ai-to-generate-fixmystreet-reports/) only generated joke titles.

**Verdict:** no ready-made model covers our task. The public ones detect 2 to 11 visual classes on Indian or Saudi roads; none speaks Polish, none knows Kraków's categories, and none can say who fixes the problem. Prompting a general vision LLM with an enum-based JSON schema is the better path, and the only one that fits in 15 hours. The datasets are useful for one thing: 10–20 sample photos to test the prompt before the demo.

---

## Open points

- The KCK „Zgłoś problem” form and its category list are behind a login. If someone on the team has a Kraków account, a screenshot of the form would replace the city's prose description in 1c.
- In the BO form, the instruction text does not say whether "Opis procesu rekrutacji" is mandatory (the asterisk is only on the screenshot). It does not matter for our schema.
- A city land-ownership map would turn "Who fixes" question 1 from a guess into a lookup. That is the pitch item already named in BRIEF.md, not something for the next 15 hours.
