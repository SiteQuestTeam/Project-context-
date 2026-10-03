---
status: accepted (supersedes ADR 0004 and ADR 0005)
---

# A social-action game replaces the HubMI core

The HubMI core (post a Need → match Helpers → AI writes a Local initiative application) was built for a partner we no longer target, and fault reporting alone is already solved by mKraków. For Smart City we build a game, like Pokémon Go but for social action: young adults do real Quests and group Raids at public places (Hubs), earn Points, Ranks and Badges, and their districts compete in a monthly league; the city sees who really acts. The problem we answer is that young adults do not know their neighbours or take part in local life, and the few who act stay invisible. With three developers and one night, the game must work well rather than sit on top of half-built old features, so Needs, Helpers, the Application draft, the KRS check, Hazard levels and photo blurring are dropped, and AI is not part of the core build.

## Consequences

- Points come only from confirmed real actions, never from activity inside the app; this keeps the spirit of ADR 0003 (trust from confirmed results).
- A Rank gives credibility, not power over other Players.
- Integrations that need the government (mObywatel, city systems) are pitch only.
