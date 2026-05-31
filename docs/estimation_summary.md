# Estimation Summary

This summary is generated from the saved estimation artifacts. It should not be edited to hardcode conclusions.

## Main Estimand

- Estimand: population average treatment effect risk difference.
- Treatment: `treatment_high_engagement_14d_median`.
- Outcome: `outcome_success`.
- Adjustment set source: `oulad_causal.dag.recommended_baseline_adjustment_set`.
- Analysis rows: 28128.

## Main Estimators

| estimator | preferred | status | estimate | 95% CI | SE | notes |
| --- | --- | --- | ---: | ---: | ---: | --- |
| regression_adjustment | False | success | 0.234926 | [0.234157, 0.235694] | 0.000392 | mean predicted potential outcome under separate logistic outcome regressions |
| stabilized_iptw | False | success | 0.233985 | [0.216530, 0.251439] | 0.008905 | stabilized IPTW Hajek-style weighted mean contrast; no default truncation |
| aipw | True | success | 0.235260 | [0.224048, 0.246471] | 0.005720 | doubly robust AIPW estimator using propensity and separate outcome nuisance models |
| nearest_neighbor_matching | False | skipped |  |  |  | poor overlap diagnostics; matching estimate not reported |

Preferred main estimate: `aipw` with risk difference 0.235260.

## Diagnostics Produced

- Effect estimates table: `data/processed/effect_estimates_main.csv`.
- Balance table: `data/processed/balance_table_main.csv`.
- Overlap plot: `reports/figures/overlap_plot.png`.
- Love plot: `reports/figures/love_plot_main.png`.
- Effective sample size after stabilized weighting: 26694.30.
- Propensity score range: 0.000240 to 0.853557.
- Propensity scores clipped for finite arithmetic: 5.
- Common support outside share: 0.000498.
- Maximum absolute SMD after weighting: 0.022340.
- Poor overlap flag: True.

## Known Limitations

- This is an observational estimate and relies on conditional exchangeability after the documented baseline adjustment set.
- Motivation, time availability, outside support, employment, and competing obligations remain unmeasured.
- VLE clicks measure platform interaction quantity, not necessarily learning quality.
- Stabilized weights are not truncated by default; poor overlap is detected and reported instead.
- Later assessment behavior and later VLE activity are intentionally excluded from the primary adjustment set because they may be post-treatment mediators.

## Automatic Warnings

- Overlap or post-weighting balance diagnostics were flagged as poor.
- Some propensity scores were clipped only for finite arithmetic; weights were not otherwise truncated.
- Nearest-neighbor matching skipped: poor overlap diagnostics; matching estimate not reported.
