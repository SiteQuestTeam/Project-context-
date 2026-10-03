# Grill: SideQuest for Smart City (3.10.2026)

Decision log from the `grill-with-docs` session. The old HubMI decisions are in [grilling-decisions.md](grilling-decisions.md); this file replaces them where they conflict.

## Round 1

- **Q1 Problem:** both. Neighbours do not know each other, and the people who do act locally are invisible (councils are full of politicians, not doers). One sentence for slide 1 is still open (Q6).
- **Q2 Players:** anyone can play, but we design for young adults. Ranks give no power: the game is fun and social engagement, not a say in decisions.
- **Q3 Actions:** actions come in different sizes, up to initiatives of several hours. Each one states how long it takes. Group actions work like Raids in Pokémon Go, but for social actions.
- **Q4 Scope:** a hackathon task, so the scope is small. Focus on gamification. The old HubMI features (Application draft, KRS, Hazard level, photo blur, Proven solutions, Organisation offers) are out.
- **Q5 Team:** Tech is Gabriel, Szymon and Patryk. Psychology is Eryk, Tomasz and Kacper.

## Round 2

- **Rank:** gives credibility, never power.
- **Q6 Slide 1:** "Young adults in Kraków do not know their neighbours and do not take part in local life. The few who do act stay invisible, so councils fill up with politicians instead of doers."
- **Q7 Actions:** two kinds, Quest (solo, small, from a ready list) and Raid (group, at a Hub, start time, stated length, minimum people). Any Player can create a Raid.
- **Q8 Hubs:** Raids happen at real public places (libraries, culture centres, parks, council offices). About 20 Hubs in Kraków for the demo.
- **Q9 Proof:** Raid = scan the Organiser's code + GPS near the Hub. Quest = photo + GPS.
- **Q10 Rewards:** built in the demo, 3 made-up local Sponsors. Rewards unlock at a Rank or Badge; they are not bought with points.

## Round 3

- **Q11 Points:** only from confirmed actions. Raid = points per confirmed hour; Quest = fixed points; Organiser bonus when the Raid reaches its minimum. Posting, liking, signing up give nothing.
- **Q12 League:** confirmed action hours per 1,000 residents, so every district has an equal chance. Monthly Seasons that reset. Idea: themed Seasons (Q16).
- **Q13 Bragging:** public profile (nickname, not real name) + share card for Instagram stories on a new Badge or Rank.
- **Q14 City view:** league map, most active Hubs, top Organisers per district (only Players who agree). Hubs can create Raids. Activity must be information for local government.
- **Q15 Polish names:** keep the current ones; the psychology team may change them later.

## Round 4

- **Q16 Themed Seasons:** the theme only adds a Season Badge and featured Quests. The league counts all hours the same.
- **Q17 Demo story:** Ola, 24, new in Grzegórzki: Quest → Badge → Raid at the library Hub → Rank + Share card → Reward → league moves → City view. The jury scans a Raid code live at a "Tauron Arena" Hub. A Raid is also a way to meet new people.
- **Q18 Demo data:** about 50 example Players and past Seasons across 18 districts, marked as examples, plus real resident numbers per district. Details later. Gabriel.
- **Q19 Stack:** keep ADR 0006 (React + TypeScript + Leaflet, FastAPI, Supabase, PWA).
- **Q20 AI:** no AI in the core build. AI photo check only if time is left. Things that need complex government integration (mObywatel, city systems) are pitch only.

## Round 5

- **Q21 In-app friends:** yes. After a Raid, Players can add the people who were there. "Neighbours" is a bad name; the name comes later.
- **Q22 Cheating:** daily Points cap + closing photo for a Raid. Needs more depth (round 6): a trusted high-Rank Player who checks and accepts proofs.
- **Q23 Scope:** Level 1 = sign-up + Home district, map with Hubs, Quests, Raids, Points/Ranks/Badges, District league, Share card, Rewards, City view. Level 2 = themed Seasons, friends, daily cap, AI photo check. Pitch only = mObywatel, city systems, Sponsor self-sign-up, push. Cut Rewards first if time runs short.
- **ADRs:** 0007 (Smart City, not HubMI) and 0008 (the game replaces the HubMI core) written; 0001, 0004, 0005 marked superseded.

## Round 6

- **Q24 Reviewer:** at a top Rank a Player can become a Reviewer. Reviews Proofs only, never people. 3 Reviewers per Proof, 2 must agree. A Reviewer who often disagrees loses the right. Rule is now: Rank gives credibility and, at the top, the right to review Proofs; never power over people.
- **Q25 Pending Points:** Quest Points wait for Reviewers. Raid Points come at once from code + GPS; taken back if the closing photo is rejected.
- **Q26 Photo privacy:** only Reviewers see Proof photos; deleted after review; the public sees only "done".

## Round 7 (WoW analysis + "Propozycje aplikacja")

- **Q27 Quest classes:** we need different classes of Quests. Eryk's example: a pipe by his block where people chain bikes. Someone visits and adds a live photo (only possible on the spot), proposing "a bike rack is missing here": passive engagement, a resident cannot fix it. Active example: cleaning a square: before photo → group Raid → after photo accepted by Reviewers. Model for the classes → round 8.
- **Q28 Raid roles:** Level 1 = roles with slots + "missing N" on the map. Multi-Raid progress bar = pitch only.
- **Q29 Points:** no points for intentions. But the scale differs by class (a bike-rack report earns less than helping clean a square), and each kind of activity is recorded separately.
- **Q30 Streaks:** none. "Welcome back" instead.
- **Q31 Ranks:** the Rank system belongs in the pitch and the project; it may not need to be built (→ round 8, because Reviewers and Rewards depend on Rank). Many reputation paths = pitch.
- **Q32 Before/after:** Raid Organiser takes before + after photos of the place; Reviewers also check for faces; then public on the Raid complete card. Quest photos stay private.
- **Q33 Rewards:** unlock, not exchange. Add cosmetic titles and avatar frames. The long reward list = one pitch slide. District league winner unlocks a "Cup discount" for its active Players.
- **Q34 Other ideas:** no mascot. Raids have rarity. Buddy for newcomers: yes. District Tamagotchi: yes, it pushes users to real change. Guilds, potential-spots radar / AR / AI quest generator, monthly card: pitch only. A Player's history of past actions on the profile: yes.

## Round 8

- **Q35 Classes:** three classes OK: Scouting (passive, the city must fix it, live photo on the spot), Quest (active, solo), Raid (active, group, before → after). But actions also need **difficulty levels**, because problems differ in how hard they are (→ round 9).
- **Q36 Grey spot:** other Players can confirm it with their own live photo; the City view sorts Grey spots by confirmations; an "after" photo turns it green. No Badge for this, but it is recorded in the Player's History (the "travel log").
- **Q37 Who fixes:** the reporter picks, a Reviewer may correct; "we can do it" → "Create Raid" with the before photo already there. But some problems need skills a normal Player lacks (welding a bike rack): they need e.g. a "craft guild" (→ round 9).
- **Q38 Tamagotchi:** Level 1 = the map itself turns grey → green. Level 2 = a district picture that turns greener.
- **Q39 Rank:** build a simple single Rank (Points threshold). Many paths = pitch.
- **Q40 Rarity:** Common (up to 5 people), Rare (5–15), Epic (15+ or the Raid turned a Grey spot green).
- **Fact found:** the org `SiteQuestTeam` already has `App` (Expo / React Native, Kacper) and `Backend` (NestJS / TypeScript, Patryk). This contradicts ADR 0002 (PWA) and ADR 0006 (React web + FastAPI) (→ round 9).

## Round 9

- **Q41 Stack:** technology does not matter for the docs; the tech team decides and the docs adapt (ADR 0009, supersedes 0002 and 0006). Only rule kept: the jury opens the app from a link.
- **Q42 Difficulty:** five levels: Copper, Silver, Gold, Platinum, Diamond (Miedź, Srebro, Złoto, Platyna, Diament). Higher level = more Points; multipliers set by the psychology team.
- **Q43 Who fixes:** Players / Guild / City. In the demo the Guild is only a label. "Craft guild" is an umbrella for many organisations; how it really works is a later, technical topic. Still open: how to tell which actions a Player can do and which need a Guild or the City (→ round 10).
- **Q44 Docs on GitHub:** a new repo `SiteQuestTeam/Docs`. **Do not push yet**: the team first reviews the final brief.

## Round 10

- **Q45 Who fixes:** the two yes/no questions (city land/permission/money → City; special skills/tools → Guild; else Players). But the system itself should know, from the location, the photo and past projects (→ round 11: conflicts with "no AI in core").
- **Q46 Difficulty:** worked out by the app, not set by the Organiser; a Reviewer may move it one level.
- **Q47 Before/after:** only where a place changes. Helping seniors with phones is not a Raid, it is a normal Quest (→ round 11: changes what Quest and Raid mean).

## Round 11

- **Q48 Quest vs Raid:** the line is "does a place change?", not "solo or group". Raid = changes a place, always before → after, usually from a Grey spot. Quest = helps people without changing a place, solo (photo + GPS) or group at a Hub (Check-in). Difficulty from time: Copper ≤15 min (+ Scouting, Confirmation), Silver ≤1 h, Gold ≤2 h, Platinum 2–4 h, Diamond = Raid that turns a Grey spot green.
- **Q49 Who fixes:** Level 1 = two yes/no questions. Level 2 = AI suggests the answer from photo and place, the Player approves. Pitch = city land map and learning from past projects.
- **Q50 Demo order:** Scouting (pipe) → group Quest at the library (seniors' phones) → Raid cleaning the square from a Grey spot (green, Diamond, Epic card) → Rank → Reward → League → City view.

## Left for later (not blocking the build)

- Name of the app is SideQuest (decided). Still open: name for in-app friends, final Polish names of game words (psychology team).
- Exact demo data, Badge and Rank thresholds, Points values, Sponsors (psychology team + Gabriel).
- Ask the PKO mentor: submission platform (Challenge Rocket or Hack Tribe) and the deadline hour.

## GitHub check

- Szymon (szymczyk71): full-stack, TypeScript and JavaScript.
- Gabriel (gabensaw): data engineer. Python, PostgreSQL, ETL.
- Patryk (P4tkry): strong in TypeScript (20 repos).
