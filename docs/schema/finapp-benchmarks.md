# finapp_benchmarks schema

Schema: `finapp_benchmarks` — external reference data for context and comparison. All tables are read-only (RLS: Auth Read Only).

All tables include: `source`, `source_url`, `notes`, `created_at` columns.

---

## Tables

### salary_by_age

BLS salary benchmarks by age group.

| Column | Type |
|--------|------|
| `age` | integer |
| `survey_year` | integer |
| `median_salary` | numeric |
| `average_salary` | numeric |
| `p10` / `p25` / `p75` / `p90` | numeric |

### salary_by_education

| Column | Type |
|--------|------|
| `education_level` | text |
| `survey_year` | integer |
| `median_weekly` | numeric |
| `median_annual` | numeric |

### net_worth_by_age

Federal Reserve SCF net worth benchmarks.

| Column | Type |
|--------|------|
| `age_min` / `age_max` | integer |
| `survey_year` | integer |
| `median_nw` / `average_nw` | numeric |
| `p25_nw` / `p75_nw` / `p90_nw` | numeric |

### retirement_by_generation

| Column | Type |
|--------|------|
| `generation` | text |
| `birth_year_min` / `birth_year_max` | integer |
| `survey_year` | integer |
| `avg_401k_balance` / `median_401k_balance` | numeric |
| `avg_ira_balance` | numeric |
| `total_savings_rate` | numeric |

### spending_by_category

BLS Consumer Expenditure Survey — maps to finapp categories.

| Column | Type | Notes |
|--------|------|-------|
| `survey_year` | integer | |
| `bls_category` | text | Original BLS category name |
| `finapp_category` | text | Mapped finapp category |
| `annual_avg` / `monthly_avg` | numeric | |
| `pct_of_total` | numeric | |
| `income_quintile` | text | |

### housing_market

| Column | Type |
|--------|------|
| `survey_year` / `survey_quarter` | integer |
| `geo_level` | text |
| `geo_name` | text |
| `median_home_price` / `avg_home_price` | numeric |
| `median_price_sqft` | numeric |
| `avg_mortgage_rate` | numeric |
| `avg_days_on_market` | integer |
| `yoy_pct_change` | numeric |
| `price_to_income_ratio` | numeric |

### inflation_cpi_annual

| Column | Type | Notes |
|--------|------|-------|
| `year` | integer | |
| `category` | text | CPI category |
| `finapp_category` | text | Mapped finapp category |
| `yoy_pct_change` | numeric | |

### federal_tax_brackets

| Column | Type |
|--------|------|
| `tax_year` | integer |
| `rate_pct` | numeric |
| `income_min` / `income_max` | numeric |
| `filing_status` | text |
| `standard_deduction` | numeric |

### ca_tax_brackets

Same structure as `federal_tax_brackets` for California state tax.

### roth_ira_rules

| Column | Type |
|--------|------|
| `tax_year` | integer |
| `filing_status` | text |
| `contribution_limit` | numeric |
| `catch_up_limit` | numeric |
| `magi_full_contribution` | numeric |
| `magi_phase_out_start` / `magi_phase_out_end` | numeric |

### fed_rates

Federal Reserve interest rates.

| Column | Type |
|--------|------|
| `rate_date` | date |
| `effective_rate` | numeric |
| `target_rate_low` / `target_rate_high` | numeric |

### mortgage_rates

| Column | Type |
|--------|------|
| `rate_date` | date |
| `rate_30yr` | numeric |
| `rate_15yr` | numeric |
