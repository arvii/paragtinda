# paragtinda

Monorepo with a Rails 8 API backend and a React + Vite + TypeScript frontend.

## Structure

- `backend/` — Rails 8 API-only app (Ruby 3.3.4, PostgreSQL)
- `frontend/` — React + Vite + TypeScript app

## Requirements

- Ruby 3.3.4 (see `backend/.ruby-version`)
- Node 22+
- Docker + Docker Compose (for PostgreSQL, or to run the whole stack)

## Running everything with Docker Compose

```
docker compose up --build
```

- Backend: http://localhost:3000
- Frontend: http://localhost:5173
- Postgres: localhost:5432

## Running locally without Docker

Start Postgres via Docker Compose, then run each app with its own toolchain:

```
docker compose up -d db

cd backend
bin/rails db:prepare
bin/rails server -p 3000

cd frontend
npm install
cp .env.example .env
npm run dev
```

The frontend calls `VITE_API_URL` (defaults to `http://localhost:3000`) at `/api/health`.
