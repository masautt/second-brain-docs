# second-brain-scripts

Interactive CLI for managing the Second Brain Supabase database — people, relationships, pay scales, schema inspection, and data validation.

Part of the [Second Brain](../README.md) ecosystem. See [full CLI docs](../docs/second-brain-scripts.md).

## What it does

- **pinapp menu** — add/update people, relationships, contact info, context tags
- **finapp menu** — pay scale analysis, finance views
- **validate** — 10+ data integrity checks (orphans, duplicates, RLS policies, etc.) with auto-fix
- **fetch** — schema inspector for Supabase
- **backup** — database dump to `second-brain-backups/`

## Setup

1. Install dependencies:

```bash
npm install
```

2. Create credentials file at `~/source/.config/supabase-creds.json`:

```json
{
  "url": "https://your-project.supabase.co",
  "serviceRoleKey": "your-service-role-key",
  "dbUrl": "postgresql://postgres.xxx:password@host:port/postgres"
}
```

3. (First time) Install Supabase helper functions:

```bash
npm run sql:exec sql/supabase-functions.sql
```

## Commands

```bash
npm run menu            # People management (pinapp)
npm run validate        # Run full validation suite
npm run validate:menu   # Pick validators interactively
npm run pay-scale       # Pay scale analysis
npm run views           # Finance views menu
npm run fetch           # Schema fetcher
npm run backup          # Database backup
npm run sql:exec        # Run a SQL file against the DB
```

## Project structure

```
src/
├── cli.ts              # Entry point
├── lib/                # Config, schema fetcher, utils
├── queries/            # Standalone query scripts
├── scripts/
│   ├── finapp/         # Finance scripts & menus
│   ├── pinapp/         # People scripts, menus, add/update/query
│   ├── utils/          # Backup, SQL exec
│   └── validators/     # 10+ integrity validators + auto-fixes
sql/                    # Supabase helper functions & migrations
ai-docs/                # Schema reference docs (pinapp + finapp)
```
