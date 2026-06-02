# Solar PV Forecasting Appendix Artifacts

This repository package contains the research artifacts supporting the manuscript:

**A Physics-Guided Two-Stage XGBoost Workflow for 5-Minute-Grid Solar PV Power Prediction Using Operational Weather and Plant Data**

The package is prepared for GitHub appendix access. It includes the active notebook, legacy notebooks, datasets used during the project, model artifacts, prediction examples, manuscript figures, metrics tables, and the compiled paper draft. Helper scripts, virtual environments, and build caches are intentionally excluded.

## Repository Layout

```text
code/
  notebooks/
    current/              Active v7 training and inference notebook
    legacy/               Earlier notebook versions and comparison notebooks

data/
  current_dataset/        Main dataset used by the active notebook and manuscript
  training_archive/       Earlier training dataset and training manifest
  prediction_examples/    Forecast-CSV input/output examples
  raw_reference_datasets/ Earlier raw/reference datasets retained for traceability

models/
  current_v7/             Active trained v7 model artifacts and metadata
  legacy_archive/         Earlier model artifacts retained for comparison/history

results/
  paper_figures/          Figures exported from the notebook workflow
  latex_figures/          Figures currently packaged with the LaTeX paper
  tables_and_metrics/     Manuscript tables, metrics JSON, and metrics audit CSV

manuscript/
  compiled_pdf/           Latest compiled PDF draft
  latex_source/           Current LaTeX source files needed to inspect paper text

docs/
  project_context/        Project context and paper asset inventory snapshots
```

## Main Entry Points

- Active notebook: `code/notebooks/current/solar_v7_main_training_and_inference.ipynb`
- Main dataset: `data/current_dataset/bycodex_realistic_43_624kw_vit_chennai_2021_2025_5min.csv`
- Active model metadata: `models/current_v7/v7_metadata.json`
- Active trained models:
  - `models/current_v7/kt_model_v7.pkl`
  - `models/current_v7/power_model_v7.pkl`
  - `models/current_v7/sensor_model_v7.pkl`
- Metrics audit: `results/tables_and_metrics/metrics_audit_2026-05-23.csv`
- Manuscript PDF: `manuscript/compiled_pdf/solar_pv_forecasting_ieee_access_draft.pdf`

## Reproducibility Notes

The notebooks are the code record in this release. Standalone helper scripts from the working project are not included because this package is meant to be a clean GitHub appendix artifact rather than a full internal workspace mirror.

The model files are Python pickle artifacts. Use them only in a trusted research environment.

Recommended Python dependencies are listed in `requirements.txt`. The original local virtual environment is not included.

## GitHub Notes

No individual file in this package is intended to exceed GitHub's 100 MB file limit. The complete package is larger than a minimal code-only repository because it includes datasets, trained models, paper figures, and raw/reference data archives for traceability.

Before final public release, choose the repository license and update `CITATION.cff` with the final manuscript DOI or repository DOI if one is issued.
