# finapp-mou-comp

Micro-frontend component that visualizes pay rates and positions from the Memorandum of Understanding (MOU) between the Teamsters and the county.

Part of the [Second Brain](../README.md) ecosystem. See [full finapp docs](../docs/finapp.md).

## What it does

Built for county employees who want to understand their pay history, compare positions across the org, and model career progression — without digging through a PDF contract.

- County switcher (LA, Orange, Riverside, San Bernardino)
- Pay rate timeline — line chart showing how rates changed over time
- Position comparison — side-by-side org chart view
- Mobile responsive
- Static export mode for GitHub Pages

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

## Import conventions

Use path aliases — never relative imports:

| Alias | Resolves to |
|-------|------------|
| `@components/...` | `src/components/...` |
| `@utils/...` | `src/utils/...` |
| `@config/...` | `src/config/...` |
| `@pages/...` | `src/pages/...` |
| `@data/...` | `src/data/...` |
| `@/...` | `src/...` |

Every import must be on a single line — no multi-line import blocks.
