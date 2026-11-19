# Wattcheck: Setup Guide

How to install, configure and run the app locally.

## Requirements

- Node.js 18+
- MongoDB 6+ (a local install on `mongodb://127.0.0.1:27017`, or a free MongoDB Atlas cluster). No replica set is needed.

## Install and run

```bash
cp server/.env.example server/.env   # set JWT_SECRET and, if needed, MONGODB_URI
npm install                          # root (concurrently)
npm run install:all                  # server + client
npm run db:setup                     # create indexes (the server also does this on start-up)
npm run seed                         # measure library + demo institutions
npm run dev                          # API :4000, app :5173
```

Open **http://localhost:5173** (not port 4000; `/api` alone is not a page).

## Configuration

Key settings in `server/.env`:

| Variable | Purpose |
|---|---|
| `MONGODB_URI` | Local `mongodb://127.0.0.1:27017` or an Atlas `mongodb+srv://…` string (URL-encode special characters in the password) |
| `MONGODB_DB` | Database name, default `energy_audit` |
| `TEST_MONGODB_DB` | Separate database wiped by `npm test`; its name must end in `_test` |
| `JWT_SECRET` | At least 16 characters |
| `ANOMALY_THRESHOLD` | Unusual-month threshold, default `0.30` |
| `LOGIN_RATE_MAX` | Login attempts allowed, default `10` |
| `COOKIE_SECURE` | `true` behind HTTPS, `false` for plain local http |

## Demo logins

After `npm run seed`. The password for all accounts is `Demo1234!`.

| Institution | Admin | Auditor |
|---|---|---|
| Greenfield Technical College | admin@greenfield.example | auditor@greenfield.example |
| Lakeview Community Hospital | admin@lakeview.example | auditor@lakeview.example |

Or use **Register here** on the login page to create a new institution.

## Tests

```bash
npm test
```

Runs the server suite (Vitest + Supertest) against the separate test database.

## Troubleshooting

| Symptom | Fix |
|---|---|
| `bad auth : authentication failed` | Wrong username/password in `MONGODB_URI`. For Atlas, use the *database user's* password. |
| `Cannot connect to MongoDB` on start-up | Start the MongoDB service, or check `MONGODB_URI`. Atlas also needs your IP in its network access list. |
| Login works on `localhost` but cookies fail behind HTTPS | Set `COOKIE_SECURE=true`. |

See [TECHNICAL.md](TECHNICAL.md) for architecture and data-storage details, or [README.md](README.md) for the documentation index.
