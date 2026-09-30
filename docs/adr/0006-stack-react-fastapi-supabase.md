# Stack: React + TypeScript PWA, FastAPI, Supabase, Linux server

The frontend is a React + TypeScript PWA with Leaflet for maps, because Patryk knows React and TypeScript well and Design is 20% of the jury score. The backend is FastAPI in Python, which the whole team knows; it owns everything that must not run in the browser: photo blurring, AI calls (API keys stay server-side) and the KRS check. Supabase provides the database (Postgres with PostGIS for "similar Needs within ~200 m"), sign-in by e-mail/Google, and photo storage in one service, which saves hours in a 24-hour build; its free plan is enough for the demo. The backend runs on a Linux server with a public address (a small VPS or a Docker host) because EgoBlur does not support Windows (ADR 0005) and the jury must open the app on their own phones.

## Considered Options

- **Python-only frontend (FastAPI + HTMX)**: the fallback if nobody knew JavaScript. Not needed.
- **Own Postgres + own auth**: more control, but hours of setup we do not have.
