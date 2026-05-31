# Results Walkthrough Draft

This draft lists the final report and presentation assets generated from saved pipeline outputs. Keep interpretation cautious and replace placeholders only after human review.

## DAG figure

- Artifact: `reports/figures/primary_dag.png`
- Sources: `reports/figures/primary_dag.png`, `data/processed/primary_dag.yaml`
- Shows: the domain-informed DAG separating baseline covariates, treatment, mediating post-treatment processes, and course success.
- Interpretation placeholder: Explain why the primary adjustment set uses pre-treatment and scheduled course-context variables only.

## Cohort flow table

- Artifact: `reports/tables/cohort_flow.csv`
- Source: `data/processed/cohort_flow_table.csv`
- Shows: the row counts retained after required joins and the primary treatment-eligibility exclusion.
- Interpretation placeholder: Summarize cohort construction and note any exclusions relevant to external validity.

## Treatment prevalence figure

- Artifact: `reports/figures/treatment_prevalence.png`
- Sources: `data/processed/oulad_analytic_cohort.parquet`
- Shows: the share of records classified as high engagement under the median, top-tertile, and top-quartile thresholds for the first 14 days.
- Interpretation placeholder: Explain the threshold definitions without implying treatment assignment was randomized.

## Discovery comparison figure

- Artifact: `reports/figures/discovery_comparison.png`
- Sources: `data/processed/discovery_hand_dag_comparison.csv`, `data/processed/discovery_stability_edges.csv`
- Shows: how many discovered skeleton edges overlap with the hand-built DAG and summary counts for unrecovered hand-DAG edges and stable repeated-subsample edges.
- Interpretation placeholder: Describe discovery as exploratory support, not a replacement for the identification plan.

## Overlap plot

- Artifact: `reports/figures/overlap_plot.png`
- Source: `reports/figures/overlap_plot.png`
- Shows: estimated propensity-score distributions for high versus lower early engagement groups.
- Interpretation placeholder: Discuss overlap diagnostics and the flagged limitations before interpreting the estimates.

## Main effect estimates table

- Artifact: `reports/tables/main_effect_estimates.csv`
- Source: `data/processed/effect_estimates_main.csv`
- Shows: regression adjustment, stabilized IPTW, preferred AIPW, and matching status for the primary risk-difference estimand.
- Interpretation placeholder: State the preferred estimate and describe it as observational under the documented assumptions.

## Robustness summary table

- Artifact: `reports/tables/robustness_summary.csv`
- Source: `reports/tables/robustness_window_threshold_summary.csv`
- Shows: AIPW estimates across early-engagement windows and treatment thresholds.
- Interpretation placeholder: Identify patterns across definitions while avoiding inflated robustness claims.

## Subgroup summary figure

- Artifact: `reports/figures/subgroup_summary.png`
- Source: `reports/tables/robustness_subgroup_placebo_sensitivity_summary.csv`
- Shows: successful subgroup estimates for pre-specified subgroup variables that passed adequacy gates.
- Interpretation placeholder: Treat subgroup differences as descriptive robustness checks, not definitive heterogeneity.
