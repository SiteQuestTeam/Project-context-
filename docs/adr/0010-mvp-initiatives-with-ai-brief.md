---
status: accepted (partly supersedes ADR 0008, which is in the `archiwizowane` branch)
---

# The MVP is Initiatives with an AI Brief, Votes on the spot and Points spent on Rewards

At half-time (Saturday evening, about 15 hours left) only empty App and Backend skeletons existed, so the full game from ADR 0008 (Scouting, Quests, Raids, Check-ins, Reviewers, District league) could not be delivered. The MVP is cut to four features from `MVP.md`: a map with the Player's Avatar; proposing an Initiative on the spot, where Claude (Sonnet 5.5) drafts a short Brief from the Live photo and at most three questions; Votes given only within about 50 m, one per Player per Initiative, with an Initiative passing at a fixed Threshold; and Points spent on Rewards, plus a landing page and logo. The game parts come back later.

## Considered options

- **Keep ADR 0008's "no AI in the core".** Rejected: the AI-drafted Brief is what makes proposing an Initiative quick and is the clearest thing to show the jury. We prompt a general vision model with our own system prompt and schema; no ready-made civic-issue model fits Kraków's categories (see `docs/research-ai-form.md`), and there is no time to train one.
- **Votes from anywhere, as `MVP.md` first said.** Rejected: "you cannot back an idea from the sofa" is our strongest answer to cheating and the thing that gets people out of the house.
- **Rewards unlocked by Rank, as BRIEF v3 said.** Rejected: a real reward for acting is what will bring most Players in, and "earn Points, spend them" is simple to show. Rank counts all Points ever earned, so spending never lowers it.

## Consequences

- The Brief never contains examples from other cities or anything else the AI cannot see or be told, so the jury cannot catch it inventing sources.
- If the AI API or the network fails on stage, the server returns a prepared Brief for the demo photo after about 8 seconds.
- Points have real value now, so cheating matters more; the MVP relies on one Vote per Player per Initiative and the 50 m rule, and the pitch names stronger checks (Reviewers, mObywatel sign-in).
- Sign-in in the MVP is a nickname only; mObywatel is pitch only.
