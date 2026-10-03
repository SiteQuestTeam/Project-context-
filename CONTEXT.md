# SideQuest

A game, like Pokémon Go but for social action, in which residents of Kraków (mostly young adults) do real actions for their neighbourhood, earn Badges and Ranks, and compete in district leagues. Built for the Smart City task at HackYeah 2026. The app speaks Polish; the Polish name of each term is given in brackets. The old HubMI glossary (Need, Helper, Application draft…) is in git history.

## People

**Player** (Gracz):
Any signed-in person who scouts, does Quests and joins or creates Raids. The game is designed for young adults, but anyone can play.
_Avoid_: user, resident, volunteer

**Organiser** (Organizator):
The Player who created a group Quest or a Raid and shows its Check-in code on the spot. Any Player can be an Organiser; it needs no Rank.
_Avoid_: leader, host, admin

## Actions

There are three classes of action. Scouting shows a problem; a Quest helps people without changing a place; a Raid changes a place.

**Scouting** (Zwiad):
A visit to a problem spot to record it with a Live photo, e.g. a pipe where people chain bikes because a bike rack is missing. Passive: the Player only shows the problem, someone else fixes it. Creates a Grey spot.
_Avoid_: report, ticket, zgłoszenie

**Quest** (Misja):
An action that helps people or the neighbourhood without changing a place, done solo or in a group, e.g. helping a neighbour carry shopping (solo) or helping seniors set up their phones at a library (group). A solo Quest is proven by a photo with GPS; a group Quest at a Hub by Check-ins.
_Avoid_: task, challenge, zadanie

**Raid** (Rajd):
A group action that changes a place, always proven by "before" and "after" photos of it, usually started from a Grey spot, e.g. "Saturday 10:00–13:00, clean the square, at least 8 people". Has a start time, a stated length and a minimum number of Players, and may list Roles. Created by any Player or by a Hub.
_Avoid_: event, initiative, meetup, wydarzenie

**Role** (Rola):
A job inside a group action with a number of places, e.g. "driver 0/1", "photographer 2/3". An action with empty places shows "missing N" on the map.
_Avoid_: position, slot, function

**Live photo** (Zdjęcie na żywo):
A photo taken with the app's own camera, on the spot (GPS within about 50 m), with the time recorded; a photo from the gallery is never accepted.
_Avoid_: upload, picture

**Grey spot** (Szare miejsce):
A place on the map with a recorded problem. It turns green when an "after" Live photo shows the problem is gone, usually at the end of a Raid.
_Avoid_: issue, need, potrzeba, usterka

**Who fixes** (Kto naprawi):
The mark on a Grey spot saying who can remove the problem: the City (its land or equipment, or it needs the city's consent or money), a Guild (special skills or tools), or Players (through a Raid). Decided by two yes/no questions in that order; a Reviewer may correct it.
_Avoid_: owner, assignee, responsible

**Guild** (Gildia):
An umbrella name for organisations with skills a normal Player lacks, e.g. craftspeople who can weld a bike rack, NGOs, firms.
_Avoid_: company, contractor, partner

**Confirmation** (Potwierdzenie):
Another Player's visit to an existing Grey spot with their own Live photo, showing the problem is still there. Recorded in the Player's History; the City view sorts Grey spots by how many Confirmations they have. It cannot be given from a distance.
_Avoid_: upvote, support, like, poparcie

**Difficulty** (Trudność):
How demanding an action is, on five levels worked out by the app, never chosen by the Organiser: Copper (Scouting, Confirmation, up to 15 min), Silver (up to 1 h), Gold (up to 2 h), Platinum (2–4 h), Diamond (a Raid that turns a Grey spot green). A Reviewer may move it one level. A higher level earns more Points. Not the same as Rarity.
_Avoid_: level, tier, rank

**Hub** (Hub):
A real public place in the city where group actions can meet: a library, a culture centre, a park, a district council office.
_Avoid_: location, spot, gym, place

**Check-in** (Odbicie):
A Player's proof of being at a group Quest or a Raid: scanning the code the Organiser shows, while the phone is near the place.
_Avoid_: attendance, confirmation

## Status

**Points** (Punkty):
What a Player earns, only for confirmed actions, set by the action's Difficulty, plus a bonus for an Organiser whose action reaches its minimum number of Players. Nothing done only inside the app (posting, liking, inviting, signing up) earns Points.
_Avoid_: XP, score, coins

**Pending Points** (Punkty w weryfikacji):
Points that wait until Reviewers accept a photo: a solo Quest's photo, or a Raid's before/after photos. Points from Check-ins come at once but are taken back if the Raid's photos are rejected.
_Avoid_: unconfirmed, locked

**Rank** (Ranga):
A Player's single level, reached at set Points thresholds. It gives credibility (others can see this Player really acts) and, at the top Ranks, the right to become a Reviewer; never power over other Players or decisions.
_Avoid_: level, role, permission

**Badge** (Odznaka):
A mark for a specific achievement, shown on the Player's profile, e.g. first Raid organised.
_Avoid_: achievement, trophy, medal

**History** (Historia):
The list on a Player's profile of every action they took part in, by class, including Confirmations. It belongs to the person and stays when they change district.
_Avoid_: log, timeline, feed

**Home district** (Dzielnica):
The one of Kraków's 18 districts a Player picks at sign-up; their actions count for it in the District league.
_Avoid_: area, neighbourhood, zone

**District league** (Liga dzielnic):
The ranking of Kraków's districts by confirmed action hours per 1,000 residents, so a small district can beat a big one.
_Avoid_: leaderboard, ranking, tabela

**Season** (Sezon):
One month of the District league; at its end the league resets and a new Season starts. A Season may have a theme, e.g. "Seniors"; the theme adds a Season Badge and featured Quests but never changes how hours count.
_Avoid_: round, period

**Share card** (Karta do udostępnienia):
A ready image of a new Badge or Rank, or of a completed Raid, that a Player can post to social media, e.g. an Instagram story. Shows the nickname, never the real name.
_Avoid_: post, screenshot

**Raid complete card** (Karta Rajdu):
The Share card of a finished Raid: before/after photos, number of people, hours, and the Raid's Rarity.
_Avoid_: certificate, summary

**Rarity** (Rzadkość):
How big a finished Raid was: Common (up to 5 people), Rare (5–15), Epic (more than 15, or the Raid turned a Grey spot green). Never random.
_Avoid_: tier, level

**Reward** (Nagroda):
Something unlocked by reaching a Rank or Badge, never bought with Points: either real, from a Sponsor (e.g. a free coffee), or cosmetic (a title such as "District Animator", an avatar frame).
_Avoid_: prize, voucher, perk

**Sponsor** (Sponsor):
A local business that offers Rewards.
_Avoid_: partner, advertiser

## Checking

**Proof** (Dowód):
What shows an action really happened: a Live photo for Scouting and Confirmation; a photo with GPS for a solo Quest; Check-ins for a group Quest; Check-ins plus "before" and "after" photos of the place for a Raid. Solo Quest photos are seen only by Reviewers and deleted after review. A Raid's before/after photos become public once Reviewers accept them and confirm no faces are visible.
_Avoid_: evidence, verification

**Reviewer** (Weryfikator):
A Player of a top Rank who reviews Proofs, never people. Each Proof goes to three Reviewers and two must agree; a Reviewer who often disagrees with the others loses the right.
_Avoid_: admin, moderator, judge

## The city

**City view** (Widok dla miasta):
What local government sees: Grey spots the City must fix, sorted by Confirmations; the District league map; the most active Hubs; and the top Organisers in each district. A Player appears there by name only if they agreed to it.
_Avoid_: admin panel, dashboard

**Official** (Urzędnik):
A person from the city or a district council who reads the City view. Does not play and has no power in the game.
_Avoid_: admin, city user
