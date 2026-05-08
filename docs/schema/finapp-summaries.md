# finapp_summaries, finapp_views, finapp_journal

Pre-aggregated and derived data — always prefer these over querying `finapp_data` directly for analytics.

See also: [finapp_data schema](./finapp-core.md)

---

## finapp_summaries

Read-only pre-aggregated tables. Generated from `finapp_data` via the finapp-etl summarize command.

### Column conventions

All summary tables share the same column pattern:

| Column | Type | Notes |
|--------|------|-------|
| dimension columns | text/int | e.g. `year`, `month`, `category` |
| `cnt` | integer | Row count — use `cnt`, NOT `count` |
| `amt` | numeric | Amount total — use `amt`, NOT `amount`, `total`, or `sum` |

Month values are always 3-letter lowercase: `jan` `feb` `mar` `apr` `may` `jun` `jul` `aug` `sep` `oct` `nov` `dec`

### Dimension codes (used in table names)

| Code | Dimension |
|------|-----------|
| `bus` | business |
| `cat` | category |
| `sub` | subcategory |
| `catsub` | category + subcategory |
| `loc` | location |
| `mo` | month |
| `wk` | week |
| `wkday` | weekday |
| `yr` | year |
| `yrmo` | year + month |
| `yrmoda` | year + month + day |
| `yrwk` | year + week |

### Segment suffixes

Every base transum table also has three segment variants:

| Suffix | Filters by |
|--------|-----------|
| `_by_recipient` | who the purchase was for |
| `_by_necessity` | need vs. want |
| `_by_ex` | ex-tagged transactions |

### Transaction summary tables (transum_*)

```
transum_bus, transum_busyr, transum_busyrmo
transum_cat, transum_catsub, transum_catsubwkday, transum_catwkday
transum_loc, transum_locyr, transum_locyrmo
transum_mo, transum_mocatwkday, transum_mowkday
transum_sub
transum_wk, transum_wkcat, transum_wkcatsub, transum_wkday
transum_yr, transum_yrcat, transum_yrcatsub, transum_yrcatwkday
transum_yrmo, transum_yrmocat, transum_yrmocatsub, transum_yrmocatwkday
transum_yrmoda, transum_yrmodacat, transum_yrmodacatsub, transum_yrmowkday
transum_yrwk, transum_yrwkcat, transum_yrwkcatsub, transum_yrwkday
```

Each of the above also has `_by_recipient`, `_by_necessity`, and `_by_ex` variants.

### Paycheck summary tables (paysum_*)

```
paysum_yr
paysum_yr_metrics
paysum_yr_by_source
paysum_yr_by_source_metrics
paysum_yrmo
paysum_yrmo_metrics
paysum_yrmo_by_source
paysum_yrmo_by_source_metrics
```

### Example usage

```sql
-- Total spending by category this year
SELECT category, amt FROM finapp_summaries.transum_yrcat
WHERE year = 2025
ORDER BY amt DESC;

-- Monthly net pay trend
SELECT year, month, amt FROM finapp_summaries.paysum_yrmo
ORDER BY year, month;
```

---

## finapp_views

Derived views over `finapp_data`.

| View | Key Columns | Notes |
|------|-------------|-------|
| `leave_balances` | `check_date`, `vacation_current`, `sick_current`, `holiday_current`, `pal_current`, earned/taken/adjust variants | Derived from paychecks table |
| `categories` | `category` | Distinct transaction categories |
| `subcategories` | `sub_category` | Distinct subcategories |
| `category_subcategories` | `category`, `sub_category` | All valid category + subcategory pairs |

---

## finapp_journal

Financial journal entries — notes and reflections tied to time periods.

### entries

| Column | Type | Notes |
|--------|------|-------|
| `id` | uuid | |
| `period_type` | text | e.g. `"month"`, `"quarter"`, `"year"` |
| `year` | integer | |
| `month` | integer | Null for annual entries |
| `quarter` | integer | Null for monthly entries |
| `title` | text | |
| `content` | text | The journal entry body |
| `created_at` / `modified_at` | timestamp | |
