# finapp

finapp is the finance domain of Second Brain: paychecks, spending, investments, budgets, and housing.

## Goals

- Replace spreadsheet workflows with queryable persistent data
- Visualize cashflow and monthly spending behavior
- Track pay scales and compensation progression

## Components

| Component | Purpose |
|-----------|---------|
| `finapp-web` | Host app for finance routes and composition |
| [`finapp-mou-comp`](../comps/finapp-mou-comp.md) | County pay scale and position visualization |
| [`finapp-cashflow-comp`](../comps/finapp-cashflow-comp.md) | Spending, income, housing, utility analysis |

## Data Domains

Primary schema: `finapp_data`

Derived schemas: `finapp_summaries`, `finapp_views`, `finapp_journal`, `finapp_benchmarks`

## Related Docs

- [CLI and ETL](../cli/second-brain-scripts.md)
- [Component docs](../comps/index.md)
- [finapp_data schema](../schema/finapp-core.md)
- [finapp summaries/views/journal](../schema/finapp-summaries.md)
- [finapp benchmarks](../schema/finapp-benchmarks.md)
