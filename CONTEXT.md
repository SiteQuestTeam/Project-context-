# Sąsiedzisko (working name)

A place where residents of Kraków post what their neighbourhood needs and what they want to do about it, and where each need is connected to the people and knowledge that can answer it. Built for the HubMI.pl task at HackYeah 2026. The app speaks Polish; the Polish name of each term is given in brackets.

## Posts

**Need** (Potrzeba):
Something that is wrong or missing in a place, posted by a Resident. A broken lamp is a Need; lonely seniors in a block are also a Need.
_Avoid_: report, issue, ticket, zgłoszenie, usterka

**Place** (Miejsce):
The single map pin every Need has.
_Avoid_: address, location, lokalizacja

**Neighbourhood-wide** (Dotyczy okolicy):
A mark on a Need that is about an area rather than the exact Place, e.g. lonely seniors on an estate. Such Needs are compared with others across the whole district, not just nearby.

**AI suggestion** (Propozycja AI):
A change the AI proposes to a Resident's post, e.g. a clearer title or a Category. It takes effect only if the Resident accepts it; the AI never changes a post on its own.
_Avoid_: auto-correction, AI edit

**Category** (Kategoria):
What a Need is about, e.g. roads, greenery, seniors. Says nothing about how dangerous it is.
_Avoid_: type, tag

**Hazard level** (Poziom zagrożenia):
How much real danger a Need poses to Residents, set separately from its Category. One of three: None (Brak), Nuisance (Utrudnienie), Danger (Zagrożenie). Needs with a higher Hazard level rank above all others, whatever their Support count. The AI proposes it; any Resident can raise it; only a Moderator can lower it.
_Avoid_: priority, urgency, severity

**Emergency** (Alarm):
A situation with danger to life or health right now, e.g. fire, smell of gas, an injured person. Not a Need: the app does not queue it, it tells the Resident to call 112.
_Avoid_: urgent Need, critical Need

**Initiative** (Inicjatywa):
An idea or an action that answers one or more Needs, proposed by a Resident or an Organisation.
_Avoid_: project, proposal, pomysł

**Support** (Poparcie):
A Resident's sign that an existing Need or Initiative matters to them too, given instead of posting a duplicate. The number of Supports is the main measure of demand.
_Avoid_: like, upvote, vote, +1, polubienie

**Comment** (Komentarz):
A reply under a Need or an Initiative. This is where Residents discuss their neighbourhood; there is no separate feed.
_Avoid_: post, discussion thread

**Discussion summary** (Podsumowanie dyskusji):
A short AI-written account of what the Comments under a Need agree on and what they dispute. The step between a discussion and an Initiative.
_Avoid_: consensus, sentiment

## Need status

**New** (Nowa):
A Need that nobody has acted on yet.

**In progress** (W toku):
A Need that has an Initiative, or that an Organisation has taken on.

**Resolved** (Rozwiązana):
A Need that the Residents who supported it have confirmed as answered. An Organisation cannot mark a Need Resolved on its own.
_Avoid_: closed, done, zamknięta

## People

**Resident** (Mieszkaniec):
A signed-in person who posts Needs, gives Support, starts or joins Initiatives, and comments. Anyone can browse without signing in, but only a Resident can act, and each Resident gives at most one Support per Need or Initiative.
_Avoid_: user, citizen, reporter

**Moderator** (Moderator):
A person who reviews posts the AI check has flagged and who alone may lower a Hazard level. During the demo this is the team; later a district council or HubMI.pl.

**Official** (Urzędnik):
A person from the city or a district council who looks at the Needs map to see where Needs gather. Reads only; does not act in the app.
_Avoid_: admin, city user

**Volunteer** (Wolontariusz):
A Resident who has joined an Initiative. Not a Helper in their own right.

## Helpers

**Helper** (Pomocnik):
Anyone or anything the app suggests to answer a Need. There are exactly three kinds: City unit, Organisation, Proven solution.
_Avoid_: service, responder, służba

**City unit** (Jednostka miejska):
A part of the city administration responsible for a type of Need, e.g. ZDMK for roads and street lamps. City units do not act inside the app: every Need shows which City unit is responsible and how to reach it. The City unit follows from the Need's Category through a fixed table; it is never guessed by the AI.
_Avoid_: department, service, urząd

**Organisation** (Organizacja):
A non-governmental group (NGO, club, parish group) that can act on Needs. Has its own account and can register itself.
_Avoid_: NGO (in the UI), partner

**Verified organisation** (Zweryfikowana):
An Organisation whose KRS number was confirmed in the public KRS register. Organisations without KRS take part without this mark.

**Track record** (Dorobek):
The number of Initiatives an Organisation led that Residents confirmed as done. The only measure of an Organisation's trustworthiness; there are no ratings.
_Avoid_: rating, score, stars, ocena

**Offer to lead** (Oferta prowadzenia):
An Organisation's declaration that it is ready to lead a given Initiative.

**Lead organisation** (Organizacja prowadząca):
The one Organisation chosen by an Initiative's author, from those that made an Offer to lead, to carry the Initiative out.
_Avoid_: contractor, wykonawca

**Proven solution** (Sprawdzone rozwiązanie):
A description of how a similar Need was already answered, in Kraków or elsewhere, so it can be reused. It states the problem, what was done, where, by whom, at what cost and in what time, and its source; without a source link it is not a Proven solution. The AI suggests matching ones when a new Need is posted. Comes either from a curated starting list or from an Initiative that was completed.
_Avoid_: best practice, case study, dobra praktyka

## Paths to the city

**Local initiative** (Inicjatywa lokalna):
Kraków's formal procedure in which Residents, directly or through an Organisation, apply to carry out a public task together with the city. Not the same as an Initiative in the app, which may or may not end in one.

**Application draft** (Szkic wniosku):
An AI-written first version of a Local initiative application, built from a Need, its Comments and its Supports.
