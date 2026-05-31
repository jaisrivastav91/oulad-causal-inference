# Causal Discovery Summary

This file is generated from the saved causal discovery artifacts. Discovery is exploratory support for the hand-built DAG, not a replacement for the identification plan.

## Scope and preprocessing

- Analytic rows: 28128.
- Variables: baseline_gender, baseline_age_band, baseline_highest_education, baseline_imd_band, baseline_disability, baseline_num_of_prev_attempts, baseline_studied_credits, baseline_registered_before_start, baseline_module_presentation_length, early_assessment_weight_14d, treatment_high_engagement_14d_median, outcome_success.
- Mixed variables were discretized before discovery: ordinal mappings for age, education, and IMD; category codes for nominal/binary fields; quantile bins for studied credits; ordered state codes for low-cardinality numeric fields.
- PC and FCI used chi-square conditional independence tests with alpha 0.01; GES used BDeu scoring on the same discrete matrix.

## Method status

| method | status | seconds | edges | note |
| --- | --- | ---: | ---: | --- |
| pc | success | 1.412 | 27 |  |
| fci | success | 1.183 | 25 |  |
| ges | success | 2.535 | 19 |  |

## What discovery supports

- `baseline_age_band` -- `outcome_success` appeared in ges and matches the hand-built DAG skeleton.
- `baseline_age_band` -- `treatment_high_engagement_14d_median` appeared in fci, ges, pc and matches the hand-built DAG skeleton; repeated-subsample pc frequency 0.70.
- `baseline_disability` -- `outcome_success` appeared in ges and matches the hand-built DAG skeleton.
- `baseline_highest_education` -- `outcome_success` appeared in fci, ges, pc and matches the hand-built DAG skeleton; repeated-subsample fci frequency 0.75.
- `baseline_imd_band` -- `outcome_success` appeared in fci, pc and matches the hand-built DAG skeleton.
- `baseline_module_presentation_length` -- `early_assessment_weight_14d` appeared in fci, ges, pc and matches the hand-built DAG skeleton; repeated-subsample pc frequency 1.00.
- `baseline_module_presentation_length` -- `outcome_success` appeared in fci, ges, pc and matches the hand-built DAG skeleton.
- `baseline_num_of_prev_attempts` -- `outcome_success` appeared in fci, ges, pc and matches the hand-built DAG skeleton; repeated-subsample ges frequency 0.80.
- `baseline_num_of_prev_attempts` -- `treatment_high_engagement_14d_median` appeared in fci, ges, pc and matches the hand-built DAG skeleton.
- `baseline_registered_before_start` -- `treatment_high_engagement_14d_median` appeared in fci, ges, pc and matches the hand-built DAG skeleton.
- `baseline_studied_credits` -- `outcome_success` appeared in fci, pc and matches the hand-built DAG skeleton.
- `outcome_success` -- `treatment_high_engagement_14d_median` appeared in fci, ges, pc and matches the hand-built DAG skeleton; repeated-subsample pc frequency 1.00.

## What discovery does not establish

- It does not establish causal truth, because the OULAD cohort remains observational and motivation, time availability, outside support, and similar constructs are unmeasured.
- It does not justify adjusting for post-treatment variables or changing the primary adjustment set.
- It does not make orientations definitive; PC, FCI, and GES orientations here are treated as exploratory, especially for undirected, circle, or bidirected endpoints.
- It does not remove sensitivity to preprocessing choices; the algorithms used a reduced, discretized representation of mixed variables.

## Noisy or unstable findings

- `baseline_gender` -- `baseline_studied_credits` in ges had edge frequency 0.55.
- `baseline_imd_band` -- `outcome_success` in pc had edge frequency 0.55.
- `baseline_registered_before_start` -- `treatment_high_engagement_14d_median` in ges had edge frequency 0.50.
- `baseline_imd_band` -- `outcome_success` in fci had edge frequency 0.45.
- `baseline_num_of_prev_attempts` -- `outcome_success` in pc had edge frequency 0.35.
- `baseline_num_of_prev_attempts` -- `outcome_success` in fci had edge frequency 0.30.
- `baseline_gender` -- `baseline_studied_credits` in pc had edge frequency 0.25.
- `baseline_age_band` -- `baseline_imd_band` in fci had edge frequency 0.20.
- `baseline_num_of_prev_attempts` -- `treatment_high_engagement_14d_median` in pc had edge frequency 0.20.
- `baseline_age_band` -- `baseline_gender` in ges had edge frequency 0.20.
- `baseline_disability` -- `outcome_success` in ges had edge frequency 0.20.
- `baseline_gender` -- `baseline_imd_band` in pc had edge frequency 0.15.

## Hand-built DAG edges not recovered

- `baseline_disability` -> `treatment_high_engagement_14d_median` was in the hand-built DAG but not recovered as a skeleton edge.
- `baseline_gender` -> `outcome_success` was in the hand-built DAG but not recovered as a skeleton edge.
- `baseline_gender` -> `treatment_high_engagement_14d_median` was in the hand-built DAG but not recovered as a skeleton edge.
- `baseline_highest_education` -> `treatment_high_engagement_14d_median` was in the hand-built DAG but not recovered as a skeleton edge.
- `baseline_imd_band` -> `treatment_high_engagement_14d_median` was in the hand-built DAG but not recovered as a skeleton edge.
- `baseline_module_presentation_length` -> `treatment_high_engagement_14d_median` was in the hand-built DAG but not recovered as a skeleton edge.
- `baseline_registered_before_start` -> `outcome_success` was in the hand-built DAG but not recovered as a skeleton edge.
- `baseline_studied_credits` -> `treatment_high_engagement_14d_median` was in the hand-built DAG but not recovered as a skeleton edge.
- `early_assessment_weight_14d` -> `outcome_success` was in the hand-built DAG but not recovered as a skeleton edge.
- `early_assessment_weight_14d` -> `treatment_high_engagement_14d_median` was in the hand-built DAG but not recovered as a skeleton edge.

## Artifact inventory

- `analysis_data`: `/Users/js/projects/oulad-causal-inference-main/data/processed/discovery_analysis_data.parquet`
- `preprocessing_map`: `/Users/js/projects/oulad-causal-inference-main/data/processed/discovery_preprocessing_map.json`
- `combined_edges`: `/Users/js/projects/oulad-causal-inference-main/data/processed/discovery_edges.csv`
- `edges_pc`: `/Users/js/projects/oulad-causal-inference-main/data/processed/discovery_edges_pc.csv`
- `edges_fci`: `/Users/js/projects/oulad-causal-inference-main/data/processed/discovery_edges_fci.csv`
- `edges_ges`: `/Users/js/projects/oulad-causal-inference-main/data/processed/discovery_edges_ges.csv`
- `adjacency_pc`: `/Users/js/projects/oulad-causal-inference-main/data/processed/discovery_adjacency_pc.csv`
- `adjacency_fci`: `/Users/js/projects/oulad-causal-inference-main/data/processed/discovery_adjacency_fci.csv`
- `adjacency_ges`: `/Users/js/projects/oulad-causal-inference-main/data/processed/discovery_adjacency_ges.csv`
- `figure_pc`: `/Users/js/projects/oulad-causal-inference-main/reports/figures/discovery_pc.png`
- `figure_fci`: `/Users/js/projects/oulad-causal-inference-main/reports/figures/discovery_fci.png`
- `figure_ges`: `/Users/js/projects/oulad-causal-inference-main/reports/figures/discovery_ges.png`
- `stability_edges`: `/Users/js/projects/oulad-causal-inference-main/data/processed/discovery_stability_edges.csv`
- `hand_dag_comparison`: `/Users/js/projects/oulad-causal-inference-main/data/processed/discovery_hand_dag_comparison.csv`
- `metadata`: `/Users/js/projects/oulad-causal-inference-main/data/processed/discovery_run_metadata.json`
- `summary`: `/Users/js/projects/oulad-causal-inference-main/docs/discovery_summary.md`
