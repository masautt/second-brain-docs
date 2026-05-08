# finapp-cashflow-comp

Micro-frontend component for personal cashflow visualization — spending vs. income, housing costs, and living expense breakdowns.

Part of the [Second Brain](../README.md) ecosystem. See [full finapp docs](../docs/finapp.md).

## What it does

The "am I making progress?" view. Shows where your money is going month to month.

- Cashflow chart — income vs. spending over time
- Housing expense breakdown (mortgage, taxes, insurance, HOA)
- Utilities tracking
- Living expense categories

## Stack

- React 19, Vite, TypeScript
- `vite-plugin-federation` (Module Federation)
- Recharts
- Supabase SDK
- Tailwind CSS

## Development

```bash
npm install
npm run dev          # standalone
npm run dev:mf       # as Module Federation remote
```

## Build

```bash
npm run build        # standard build
npm run build:static # GitHub Pages export (static data)
```

## Data

Reads from the `finapp_data` Supabase schema (transactions, housing, paychecks). Data is populated via [finapp-etl](../docs/second-brain-scripts.md).
