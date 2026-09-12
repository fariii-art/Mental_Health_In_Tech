# Understanding Mental Health in Tech

**Workplace Support and Openness Among Tech Workers**

## Project Overview

Analysis of the OSMI (Open Sourcing Mental Illness) Mental Health in Tech Survey, combined 2017–2021. This project explores how workplace mental-health support relates to treatment-seeking behavior across survey years, regions, and company types.

## Team

- Maria Zaman
- Masooma
- Faryal

## Research Question

How has the relationship between workplace mental-health support (benefits, workplace resources) and treatment-seeking changed across survey years (2017–2021), and how does it vary by region and company type?

## Dataset

- **Source:** OSMI Mental Health in Tech Survey
- **Years:** 2017–2021
- **Respondents:** 1,836
- **Tables:** 5 (companies, country, gender, respondents, survey_responses)

## Tools

- PostgreSQL 16
- pgAdmin 4

## Key Findings

| Finding | Result |
|---|---|
| Overall treatment-seeking rate | **58.9%** (1,077 of 1,829) |
| Family history → treatment | **77.7%** vs. 29.7% (48-point gap) |
| Benefits → treatment | **70.5%** vs. 45.9% (25-point gap) |
| Region range | 68.1% (North America) → 10% (Middle East) |
| Tech vs. non-tech | 59.4% vs. 58.5% (<1 point) |
| Employer openness trend | 28.4% (2019) → 21.4% (2021) |
| Benefits ↔ Treatment correlation | **r = 0.96** |

## SQL Techniques Used

- **JOINs** across 3+ tables (respondents, country, companies, survey_responses)
- **CTEs** for readable step-by-step logic
- **Window functions:** `LAG()` for year-over-year change, `RANK()` for ordering years
- **Statistical function:** `CORR()` for Pearson correlation
- **FILTER (WHERE ...)** for conditional counting
- **Data validation:** row counts and join-integrity checks

## Limitations

- Sample size drops sharply in later years (756 in 2017 → 131 in 2021)
- Several regions have very small samples (Middle East n=10, Africa n=20)
- Correlation (r = 0.96) is based on only 5 yearly data points
- No formal significance testing performed — findings are descriptive associations

## How to Reproduce

1. Install PostgreSQL 16 + pgAdmin 4
2. Create database: `mental_health_tech`
3. Run the `CREATE TABLE` statements in `sql/analysis.sql`
4. Import CSV files from `data/` into their matching tables
5. Run each query in `sql/analysis.sql`

