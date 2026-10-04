# SideQuest

An app, like Pokémon Go but for social action, in which residents of Kraków (mostly young adults) propose Initiatives for their neighbourhood, support other people's Initiatives on the spot, report ordinary municipal faults through KCK, and earn Points they spend on Rewards. Built for the Smart City task at HackYeah 2026. The app speaks Polish; the Polish name of each term is given in brackets.

The MVP terms come first. The game terms (Scouting, Quest, Raid…) are kept at the end under "Later": they are not part of the MVP and come back only if there is time. The old HubMI glossary (Need, Helper, Application draft…) is in git history.

## People

**Player** (Gracz):
Any signed-in person who proposes Initiatives and gives Votes. The app is designed for young adults, but anyone can play.
_Avoid_: user, resident, volunteer

**Initiator** (Inicjator):
The Player who proposed an Initiative.
_Avoid_: author, owner, reporter

**Avatar** (Awatar):
The Player's figure on the map, at their real GPS position. Initiatives near the Avatar can be voted on.
_Avoid_: marker, pin, character

## Initiatives

**Initiative** (Inicjatywa):
A Player's proposal to change something in the neighbourhood, e.g. "a bike rack at the library entrance". Proposed on the spot with a Live photo, described in a Brief, and shown on the map, where other Players support it with Votes. It is "Collecting votes" (Zbiera głosy) until it reaches the Threshold, then "Passed" (Przeszła) and goes to whoever the Brief says fixes it. Not a City incident: a City incident needs repairing, not a vote. Never on private land (a house, garden, shop or firm); a housing cooperative's or a parish's yard is fine.
_Avoid_: project, idea, issue, report, need, potrzeba, wniosek

**Threshold** (Próg):
The number of Votes at which an Initiative passes. The same for every Initiative (10 in the demo).
_Avoid_: goal, quorum, limit

**Brief** (Brief):
The short description of an Initiative: title, category (one of the nine categories of Kraków's Civic Budget), the problem, the proposed action, why it matters, the resources needed (people, tools, transport) and Who fixes; the AI asks at most two questions (the concrete action, the resources), each with a "why I ask" line and suggested answers that only fill in details of the Player's own idea. The Player edits and accepts the Brief before it is published. A City incident has no Brief: it has KCK report fields. It never contains examples from other cities or anything else the AI cannot see or be told.
_Avoid_: form, application, SWOT, summary

**Live photo** (Zdjęcie na żywo):
A photo taken with the app's own camera, on the spot (GPS within about 50 m), with the time recorded; a photo from the gallery is never accepted. A new photo is needed when a face is its main subject or a licence plate is readable; passers-by in the background are fine, because the law allows showing a person who is only a detail of a larger whole (art. 81 of the Polish copyright act).
_Avoid_: upload, picture

**Who fixes** (Kto naprawi):
The part of an Initiative's Brief saying who can carry out the Initiative: the City (its land or equipment, or it needs the city's consent or money) or Players. Decided by one yes/no question; the AI suggests the answer with a reason and the Player confirms it.
_Avoid_: owner, assignee, responsible

**Vote** (Głos):
A Player's support for an Initiative ("I back this idea"), given only on the spot, within about 50 m of the Initiative. One Vote per Player per Initiative. It cannot be given from a distance.
_Avoid_: like, upvote, poparcie, confirmation

**Possible danger** (Możliwe zagrożenie):
A warning the AI gives when a Live photo (or the Player's words) shows a concrete sign that someone may get hurt now: fire, smoke, an injured person, an accident, something collapsing, a broken, fallen, sparking or low-hanging wire, or a smell of gas the Player mentions. Overhead tram and power lines high above the street are not one. The app shows what the AI saw and asks whether it is really happening: if the Player confirms, the report ends with the advice to move away and call 112; if not, the report goes on, because the AI can be wrong.
_Avoid_: emergency, alert, alarm

## City incidents and KCK

**City incident** (Usterka):
An existing municipal fault that should be handled by the City, e.g. a pothole, damaged pavement, broken street equipment, pollution, greenery problem or animal-related issue. It is **not an Initiative** and does not collect Votes. After the Live photo the AI suggests whether it sees a City incident or an Initiative, with a reason, and the Player confirms it; when the AI is sure it sees a City incident, the Player cannot turn it into an Initiative, unless the Player proposes a change bigger than a repair (e.g. "a new pavement along the whole street"). For a City incident the AI asks no questions: it proposes one of five KCK categories, a title (`summary`, up to 60 characters) and a short description (`description`, up to 500); the address is derived from GPS. In the MVP all City incidents are prepared in SideQuest and sent to Krakowskie Centrum Kontaktu (KCK) only after the Player reviews the generated data and explicitly taps “Wyślij do KCK”.
_Avoid_: Initiative, Brief, Vote, Threshold, Who fixes, Defect, Grey spot

**KCK** (Krakowskie Centrum Kontaktu):
The official Kraków reporting channel used by SideQuest for City incidents. The Player never chooses the municipal department. SideQuest sends anonymous reports in the MVP and stores the returned KCK `incidentId`. Technical integration rules: [docs/kck-integration.md](docs/kck-integration.md).

**Interest** (Zainteresowanie):
A Player's report of a City incident that is already on the map, or of an Initiative that has already Passed, after the Player confirms it is the same one. It is not sent to KCK, so the City gets no duplicate. It earns fewer Points than a new report, once per Player per City incident or Initiative, and puts it in the Player's History. For an Initiative still collecting votes the Player gives a Vote instead.
_Avoid_: duplicate, like, confirmation

**History** (Historia):
The list on a Player's profile of their own Initiatives and City incidents (with the KCK number), including those they showed Interest in, each with its status.
_Avoid_: log, timeline, feed

## Status

**Points** (Punkty):
What a Player earns for real civic action: proposing an Initiative (many), giving a Vote (few), successfully submitting a City incident to KCK, and showing Interest in a City incident or a passed Initiative (few). A City incident earns Points only after KCK accepts it and returns an `incidentId`; preparing a draft or a failed/unconfirmed submission earns nothing. The Initiator and every Player who voted also receive a bonus when an Initiative passes. A Player spends Points on Rewards. Nothing done only inside the app (liking, inviting, signing up) earns Points.
_Avoid_: XP, score, coins, credits, kredyty

**Rank** (Ranga):
A Player's single level, reached at set thresholds of all Points ever earned. Spending Points never lowers it. It gives credibility (others can see this Player really acts), never power over other Players or decisions.
_Avoid_: level, role, permission

**Reward** (Nagroda):
Something a Player gets by spending Points: either real, from a Sponsor (e.g. a free coffee), or cosmetic (a title such as "District Animator", an avatar frame).
_Avoid_: prize, voucher, perk

**Sponsor** (Sponsor):
A local business that offers Rewards.
_Avoid_: partner, advertiser

## Later (not in the MVP)

**Completed Initiative** (Zrealizowana inicjatywa):
A passed Initiative that has really been carried out, shown on the profiles of its Initiator and voters, not on the map.
_Avoid_: done, closed, finished

**Guild** (Gildia):
An umbrella name for organisations with skills a normal Player lacks, e.g. craftspeople who can weld a bike rack, NGOs, firms. Would come back as a third answer to Who fixes.
_Avoid_: company, contractor, partner

**Organiser** (Organizator):
The Player who created a group Quest or a Raid and shows its Check-in code on the spot.
_Avoid_: leader, host, admin

**Scouting** (Zwiad):
A visit to a problem spot to record it with a Live photo. Passive: the Player only shows the problem, someone else fixes it. Creates a City incident.
_Avoid_: report, ticket, zgłoszenie

**Quest** (Misja):
An action that helps people or the neighbourhood without changing a place, done solo or in a group, e.g. helping seniors set up their phones at a library.
_Avoid_: task, challenge, zadanie

**Raid** (Rajd):
A group action that changes a place, proven by "before" and "after" photos of it, e.g. "Saturday 10:00–13:00, clean the square, at least 8 people".
_Avoid_: event, meetup, wydarzenie

**Role** (Rola):
A job inside a group action with a number of places, e.g. "driver 0/1".
_Avoid_: position, slot, function

**Difficulty** (Trudność):
How demanding an action is, on five levels worked out by the app: Copper, Silver, Gold, Platinum, Diamond. A higher level earns more Points.
_Avoid_: level, tier, rank

**Hub** (Hub):
A real public place in the city where group actions can meet: a library, a culture centre, a park.
_Avoid_: location, spot, place

**Check-in** (Odbicie):
A Player's proof of being at a group action: scanning the code the Organiser shows, while the phone is near the place.
_Avoid_: attendance, confirmation

**Badge** (Odznaka):
A mark for a specific achievement, shown on the Player's profile.
_Avoid_: achievement, trophy, medal

**Home district** (Dzielnica):
The one of Kraków's 18 districts a Player picks at sign-up.
_Avoid_: area, neighbourhood, zone

**District league** (Liga dzielnic):
The ranking of Kraków's districts by confirmed action hours per 1,000 residents, reset every monthly Season.
_Avoid_: leaderboard, ranking, tabela

**Share card** (Karta do udostępnienia):
A ready image of a new Badge, Rank or finished action that a Player can post to social media. Shows the nickname, never the real name.
_Avoid_: post, screenshot

**Reviewer** (Weryfikator):
A Player of a top Rank who reviews Proofs, never people. Each Proof goes to three Reviewers and two must agree.
_Avoid_: admin, moderator, judge

**City view** (Widok dla miasta):
What local government sees: problems the City must fix, sorted by support, and where people are most active.
_Avoid_: admin panel, dashboard

**Official** (Urzędnik):
A person from the city or a district council who reads the City view. Does not play and has no power in the game.
_Avoid_: admin, city user
