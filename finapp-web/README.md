# finapp-web

The finance app MFE host. Handles routing, auth, and shared layout for all finapp micro-frontend components.

Part of the [Second Brain](../README.md) ecosystem. See [full finapp docs](../docs/finapp.md).

## What it does

- Entry point for the financial information application
- Composes `finapp-mou-comp` and `finapp-cashflow-comp` via Module Federation
- Connects to Supabase `finapp_data` schema
- Handles auth (protected routes)

## Components it hosts

| Component | Purpose |
|-----------|---------|
| [finapp-mou-comp](../finapp-mou-comp/) | Pay scale & MOU visualizer |
| [finapp-cashflow-comp](../finapp-cashflow-comp/) | Cashflow & housing |

## Stack

- React 19, Vite, TypeScript
- Supabase SDK
- Recharts
- Tailwind CSS
- `vite-plugin-federation`

## Development

```bash
npm install
npm run dev
```

## Data

Reads from the `finapp_data` Supabase schema. Data is populated via [finapp-etl](../docs/second-brain-scripts.md).
