# Decisions Log

<!-- BEGIN GENERATED DATA VALIDATION DECISION -->

## 2026-05-29 Generated Data Validation Decision

- Ran the deterministic raw OULAD validation stage against `/Users/js/projects/oulad-causal-inference-main/data/raw/anonymisedData.zip`.
- Treated the seven standard OULAD CSV files as the required raw ingestion surface.
- Required exact standard column names and reported mismatches rather than renaming columns.
- Checked duplicate keys only for tables with expected one-row-per-key structure; `studentVle` repeated activity rows were summarized but not treated as duplicate-key failures.
- Wrote validation metadata to `data/metadata/` and refreshed the generated data audit in `docs/data_dictionary.md`.
- Did not start cohort construction, treatment definition, outcome coding, or causal adjustment.
- Validation status: passed.

<!-- END GENERATED DATA VALIDATION DECISION -->
