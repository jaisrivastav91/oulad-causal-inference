# Identification Plan

This document states the primary causal estimand, treatment and outcome definitions, adjustment strategy, and validity assumptions for the OULAD early-engagement analysis. It is the human-readable companion to the machine-readable DAG in `data/processed/primary_dag.yaml`.

## Research Question

Among students in the same broad course context, how would the probability of course success differ under high versus lower early online engagement during the first 14 days of a module presentation?

This is an observational, intervention-style question. The goal is not to predict success from clicks, but to estimate an assumption-dependent average treatment effect after adjusting for documented pre-treatment covariates.

## Primary Estimand

- **Estimand:** population average treatment effect (ATE) as a risk difference.
- **Treatment:** `treatment_high_engagement_14d_median` — binary indicator for high cumulative VLE activity during days 0 through 13, defined within each module-presentation using the presentation-specific median of `early_clicks_14d`.
- **Outcome:** `outcome_success` — 1 for Pass or Distinction, 0 for Fail or Withdrawn.
- **Unit of analysis:** student × module-presentation record in the analytic cohort (`data/processed/oulad_analytic_cohort.parquet`).

The primary estimate targets a **total effect** of early engagement on success. Variables on the post-treatment pathway are not adjusted for in the main specification.

## Hand-Built DAG

The domain-informed DAG separates:

- **Baseline confounders:** demographics, region, education, deprivation band, disability, prior attempts, studied credits, registration timing, and module-presentation context.
- **Scheduled course context:** early assessment count, type, and weight during days 0 through 13.
- **Treatment:** high 14-day early engagement.
- **Mediating processes:** later assessment behavior and later participation (represented in the DAG but not observed in the primary adjustment set).
- **Outcome:** final course success.

Key artifacts:

- `data/processed/primary_dag.yaml`
- `reports/figures/primary_dag.png`
- `data/processed/dag_variable_availability.csv`

## Primary Adjustment Set

The primary adjustment set comes from `oulad_causal.dag.recommended_baseline_adjustment_set()` and is saved in `primary_dag.yaml` under `recommended_adjustment_set`. It includes:

| Category | Columns |
| --- | --- |
| Demographics and background | `baseline_gender`, `baseline_region`, `baseline_age_band`, `baseline_highest_education`, `baseline_imd_band`, `baseline_disability` |
| Academic history and load | `baseline_num_of_prev_attempts`, `baseline_studied_credits` |
| Registration timing | `baseline_date_registration`, `baseline_missing_date_registration`, `baseline_registered_before_start` |
| Module context | `baseline_module_presentation`, `baseline_module_presentation_length` |
| Scheduled early assessment load | `early_assessment_count_14d`, `early_assessment_weight_14d`, `early_assessment_cma_count_14d`, `early_assessment_tma_count_14d`, `early_assessment_exam_count_14d` |

### Variables intentionally excluded from primary adjustment

The following are treated as post-treatment or on the mediation pathway and are **not** included in the main adjustment set:

- Later assessment submissions, scores, and banked status
- Later VLE activity beyond the 14-day engagement window

Including them would risk blocking part of the effect of early engagement and would not identify the same total-effect estimand.

## Identification Assumptions

The primary estimate is interpreted under standard observational assumptions:

1. **Consistency:** high versus lower early engagement is well defined by the within-presentation median threshold on cumulative days 0–13 VLE clicks.
2. **Positivity:** for each level of the adjustment set, both treatment groups have non-zero probability. Overlap is checked empirically; see `docs/estimation_summary.md` and `reports/figures/overlap_plot.png`.
3. **Conditional exchangeability:** no unmeasured confounding of early engagement and success after adjusting for the baseline set above, given the DAG.
4. **Correct timing:** adjustment is limited to variables fixed or scheduled before or during the early engagement window and not affected by treatment in ways that would make them mediators.

## Main Validity Threats

The DAG includes an explicit latent placeholder for **motivation, time availability, outside support, and competing obligations**. These constructs are unmeasured in OULAD and remain the main threat to exchangeability.

Other limitations:

- VLE clicks measure platform activity quantity, not learning quality.
- Module presentations differ in structure; within-presentation normalization and module-presentation covariates address but do not remove all contextual heterogeneity.
- The estimate should be read as assumption-dependent observational evidence, not randomized proof of causality.

## Estimation and Supporting Analyses

Primary estimators (see `docs/estimation_summary.md`):

- Regression adjustment
- Stabilized IPTW
- AIPW (preferred doubly robust estimate)

Diagnostics: balance table, overlap plot, love plot.

Exploratory support:

- Causal discovery on a reduced variable set (`docs/discovery_summary.md`) — used to compare against the hand-built skeleton, not to replace this plan.
- Robustness across engagement windows and thresholds (`docs/robustness_summary.md`).

## Related Code

- DAG specification: `src/oulad_causal/dag.py`
- Cohort and treatment construction: `src/oulad_causal/cohort.py`, `src/oulad_causal/features.py`
- Primary estimation: `src/oulad_causal/estimation.py`
