---
status: accepted (supersedes ADR 0002 and ADR 0006)
---

# The tech team owns the stack; the docs follow the code

The planning docs chose a React PWA with FastAPI and Supabase (ADR 0002, ADR 0006), but at the event the tech team started `SiteQuestTeam/App` with Expo / React Native and `SiteQuestTeam/Backend` with NestJS / TypeScript. Technology is their call: the docs describe the game and its rules, and adapt to whatever stack the code uses. One requirement stays from ADR 0002 because the demo depends on it: the jury must be able to open the app from a link on their own phones and scan a Raid code live.
