# second-brain-scripts and finapp-etl

The CLI backbone of Second Brain.

| Tool | Runtime | Purpose |
|------|---------|---------|
| `second-brain-scripts` | Node.js | DB management, validation, schema inspection |
| `finapp-etl` | Deno | Google Sheets to Supabase sync |

## second-brain-scripts

Primary capabilities:

- pinapp data management (add/update/query)
- finapp views and pay scale analysis
- validation suite and auto-fix menu
- schema fetch, SQL execution, backup workflows

Common commands:

```bash
npm run menu
npm run validate
npm run validate:menu
npm run pay-scale
npm run views
npm run fetch
npm run backup
npm run sql:exec
```

## finapp-etl

Primary capabilities:

- Sync finance datasets from Google Sheets to Supabase
- Rebuild summary tables used for analytics
- Inspect/export synchronized data

Run command:

```bash
deno run --allow-net --allow-read --allow-env --allow-write --allow-sys cli.ts
```

## Related Docs

- [Data Pipeline](../architecture/data-pipeline.md)
- [Schema Overview](../schema/overview.md)
