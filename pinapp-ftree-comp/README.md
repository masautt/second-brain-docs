# pinapp-ftree-comp

Micro-frontend component for visualizing your family tree and managing personal contacts.

Part of the [Second Brain](../README.md) ecosystem. See [full pinapp docs](../docs/pinapp.md).

## What it does

- Canvas-based family tree — drag, zoom, pan with XYFlow
- Person detail panel — contacts, key dates, relationships
- Context tagging — see who belongs to which part of your life (family, work, friends, etc.)
- Full-text search and filter
- Contacts list view (all people)
- Auth guard (login required)
- Static data fallback for offline / demo mode

## Stack

- React 19, Vite, TypeScript
- `vite-plugin-federation` (Module Federation)
- @xyflow/react (graph canvas)
- Supabase SDK
- Tailwind CSS
- Vitest + Testing Library

## Development

```bash
npm install
npm run dev          # standalone
npm run dev:mf       # as Module Federation remote
```

## Testing

```bash
npm run test
```

## Build

```bash
npm run build        # standard build
npm run build:static # static data export
```

## Data

Reads from the `people` and `property` Supabase schemas. Managed via the [second-brain-scripts](../docs/second-brain-scripts.md) CLI (add/update people, relationships, contexts).
