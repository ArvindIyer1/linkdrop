# linkdrop

A tiny shared reading list. Paste a link, say why it is worth reading. Everyone with the address sees the 20 newest links, newest first.

One Node.js process and one PostgreSQL table. No framework, one dependency (`pg`).

## Requirements

- Node.js 20 or newer
- PostgreSQL 14 or newer

## Run it locally

```bash
npm install
cp .env.example .env        # then edit PG_URL
export $(cat .env | xargs)
psql "$PG_URL" -f db/schema.sql
npm start
```

The app listens on port 3000. Open http://localhost:3000 and drop a link.

## Configuration

| Variable | What it is |
|---|---|
| `PG_URL` | PostgreSQL connection string, e.g. `postgresql://user:password@host:5432/linkdrop` |
| `HOST` | Interface to listen on (optional) |

## Health check

`GET /healthz` answers `ok` once the process is up.
