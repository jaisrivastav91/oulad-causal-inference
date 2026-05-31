# Reproducibility Runbook

This runbook documents how to reproduce the saved OULAD causal pipeline outputs from raw data.

## Prerequisites

- Python 3.10 or newer
- Official OULAD archive at `data/raw/anonymisedData.zip`, or the seven extracted CSV files under `data/raw/`

## Environment setup

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python -m pip install -e .
```

## Full pipeline

```bash
make all
```

Stages run in order:

1. `make validate-data` — raw audit to `data/metadata/`
2. `make build-cohort` — analytic cohort, DAG artifacts, cohort figures
3. `make run-discovery` — PC, FCI, GES discovery outputs
4. `make run-estimation` — primary effect estimates and diagnostics
5. `make run-robustness` — window/threshold, subgroup, placebo, sensitivity checks
6. `make build-assets` — report tables, figures, and draft interpretation files
7. `make health-check` — verify expected artifacts exist

## Verification

```bash
make health-check
make test
make lint
```

## Notebook review

After the pipeline succeeds, execute the review notebooks against saved artifacts:

```bash
.venv/bin/jupyter nbconvert --to notebook --execute --inplace notebooks/01_data_audit.ipynb
.venv/bin/jupyter nbconvert --to notebook --execute --inplace notebooks/02_dag_and_discovery_review.ipynb
.venv/bin/jupyter nbconvert --to notebook --execute --inplace notebooks/03_effect_estimation_review.ipynb
.venv/bin/jupyter nbconvert --to notebook --execute --inplace notebooks/04_presentation_figures.ipynb
```

## Notes

- Raw OULAD data are local-only and are not committed to git.
- Generated outputs live under `data/processed/`, `reports/`, and `docs/`.
- Override raw data location with `--raw-source` or `OULAD_RAW_DATA_DIR` when needed.
