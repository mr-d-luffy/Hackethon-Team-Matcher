# Hackathon Team Matcher (PS-03)

A platform to help students find compatible hackathon teammates based on skills, roles, experience, and interests.

## Docs

Read in this order:

1. `PRD.md` — what we're building and why
2. `architecture.md` — tech stack, folder structure, API, DB schema
3. `design.md` — colors, fonts, typography, component patterns
4. `rules.md` — do's and don'ts
5. `phases.md` — build plan broken into phases
6. `memory.md` — living progress log (update every session!)

## Tech stack

| Layer          | Technology                     |
| --------------- | -------------------------------- |
| Frontend        | Svelte (SvelteKit) + Tailwind CSS |
| Backend         | Node.js + Express.js             |
| Database / Auth | Supabase (PostgreSQL)            |

## Prerequisites

- Node.js 18+ and npm
- A free [Supabase](https://supabase.com) account

## Getting started

### 1. Supabase

1. Create a project at [supabase.com](https://supabase.com).
2. Run the SQL in `architecture.md` §6 to create tables and enable RLS.
3. Copy your **Project URL**, **anon key**, and **service_role key** — you'll need these for both the backend and frontend `.env` files.

### 2. Backend

```bash
cd server
cp .env.example .env   # fill in SUPABASE_URL, SUPABASE_SERVICE_ROLE_KEY, PORT
npm install
npm run dev
```

| Variable                   | Description                                  |
| --------------------------- | ----------------------------------------------- |
| `SUPABASE_URL`              | Your Supabase project URL                      |
| `SUPABASE_SERVICE_ROLE_KEY` | Supabase service role key (server-side only — never expose to the client) |
| `PORT`                      | Port the Express server listens on (default `3000`) |

### 3. Frontend

```bash
cd client
cp .env.example .env   # fill in PUBLIC_SUPABASE_URL, PUBLIC_SUPABASE_ANON_KEY, PUBLIC_API_URL
npm install
npm run dev
```

| Variable                    | Description                          |
| ----------------------------- | --------------------------------------- |
| `PUBLIC_SUPABASE_URL`         | Your Supabase project URL             |
| `PUBLIC_SUPABASE_ANON_KEY`    | Supabase anon/public key              |
| `PUBLIC_API_URL`              | URL of the running backend (e.g. `http://localhost:3000`) |

### 4. Run the app

| Service  | URL                          |
| -------- | ------------------------------ |
| Frontend | http://localhost:5173 (default) |
| Backend  | http://localhost:3000 (default) |

Start the backend first, then the frontend, so `PUBLIC_API_URL` has something to talk to.

## Project structure

```
server/     # Node.js + Express backend, Supabase service-role access
client/     # SvelteKit + Tailwind frontend, Supabase anon-key access
```

See `architecture.md` for the full folder breakdown, API routes, and database schema.

## Contributing

- Follow the conventions in `rules.md` before opening a PR.
- Update `memory.md` at the end of every working session with what changed and what's next.
- Check `phases.md` to see which phase is currently active before starting new work.
