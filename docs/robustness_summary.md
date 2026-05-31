# Robustness Summary

This summary is generated from saved robustness artifacts. Interpret these checks as sensitivity and diagnostic evidence, not as new primary causal claims.

## Primary Reference

- Primary estimand retained: high 14-day median engagement on course success.
- Primary AIPW risk-difference estimate in the robustness stage: 0.235260.
- Matching is disabled in robustness grids; regression adjustment and IPTW companion rows remain in `data/processed/robustness_estimates_long.csv`.

## Treatment Window and Threshold Checks

| window_days | threshold_name | status | estimate | n | poor_overlap |
| --- | --- | --- | ---: | ---: | --- |
| 7 | median | success | 0.203618 | 28128 | True |
| 7 | top_tertile | success | 0.194479 | 28128 | True |
| 7 | top_quartile | success | 0.196320 | 28128 | True |
| 14 | median | success | 0.235260 | 28128 | True |
| 14 | top_tertile | success | 0.218716 | 28128 | True |
| 14 | top_quartile | success | 0.218022 | 28128 | True |
| 21 | median | success | 0.236357 | 27913 | True |
| 21 | top_tertile | success | 0.224888 | 27913 | True |
| 21 | top_quartile | success | 0.219158 | 27913 | True |

## Pooled Versus Stratified Environment Check

| section | status | estimate | n | difference_from_pooled |
| --- | --- | ---: | ---: | ---: |
| pooled_primary | success | 0.235260 | 28128 | 0.000000 |
| stratified_weighted_mean | success | 0.235408 | 28128 | 0.000149 |

## Subgroups, Placebos, and Sensitivity

- Subgroups are reported only where sample size, treatment variation, and outcome variation are adequate.
- Placebo outcomes use pre-treatment quantities: registered before start, any prior attempts, and disability.
- The sensitivity grid is an illustrative additive bias calculation, not a formal Rosenbaum bound or E-value.
- Combinations explaining away the primary point estimate: 0.

## Skipped Checks

- subgroup: No Formal quals (n=272 below minimum 500)
- subgroup: Post Graduate Qualification (n=293 below minimum 500)

## Cautions

- These estimates remain observational and rely on measured baseline adjustment.
- Unmeasured motivation, available study time, outside support, and competing obligations remain plausible confounders.
- Module-presentation and subgroup estimates are descriptive robustness checks and should not be overinterpreted as definitive heterogeneity.
