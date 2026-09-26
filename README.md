# Al-Hidayah Web Platform

An academic Islamic companion web project co-developed by Arslan Tariq (24P-0610) and Arif Ali (24P-0736), FAST NUCES.

## Source scope

- Flask API routes and a JavaScript/HTML/CSS frontend.
- PostgreSQL schema with relational constraints and triggers.
- Registration/login with bcrypt password hashing and JWT handling.
- Prayer/fasting tracking, Quran progress and other companion features in source.
- Optional Anthropic Claude API integration for chat.

These are implemented source components, not proof of a complete production deployment or measured latency.

## Local setup prerequisites

```bash
git clone https://github.com/arslantariq364/al-hidayah-platform.git
cd al-hidayah-platform
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

Use a local PostgreSQL instance and inspect `schema.sql` before applying it. Configure DB_NAME, DB_USER, DB_PASS, DB_HOST, DB_PORT and a strong JWT_SECRET through the process environment. ANTHROPIC_API_KEY is optional. Merely creating a .env file does not load it: this source does not call a dotenv loader.

## Known integration/security work

- Flask frontend/template paths refer outside the current flat repository layout; repair those paths or arrange the expected directories before testing the UI.
- Some route table names do not match schema names; reconcile them before assuming all features work end to end.
- Remove the published fallback signing value and require a strong JWT_SECRET. Any deployment that used that fallback must rotate it and invalidate affected sessions.
- Restrict CORS, disable debug mode for deployment, validate request data and add endpoint tests.
- The database helper opens a connection per operation; it is not a connection pool.

Do not deploy this snapshot as production-ready. No sub-95ms query benchmark, verified normalization proof or uptime guarantee is provided. Passwords are hashed, not encrypted. This documentation review does not change implementation or live credentials.
