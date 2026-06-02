# Solar PV Power Forecasting with Physics-Guided XGBoost

This repository contains a solar power forecasting project built around a 43.624 kW photovoltaic plant case study at VIT Chennai, Tamil Nadu, India. The core idea is a two-stage XGBoost workflow that combines weather inputs, solar-geometry features, cloud-cover information, and plant-aware constraints to predict 5-minute-grid PV power output.

The repository is packaged as a standalone public project. It includes the main notebooks, datasets, trained models, exported figures, and evaluation artifacts needed to inspect the workflow and results in a clean, self-contained form.

## Project Overview

- Forecast target: 5-minute-grid AC PV power output
- Plant scale: 43.624 kW
- Site: VIT Chennai, Tamil Nadu, India
- Modeling approach:
  Stage 1 estimates a clearness-index-like irradiance behavior from weather, cloud, and solar-position features.
  Stage 2 predicts plant power using the reconstructed irradiance signal plus operational weather and plant-context features.
- Primary tooling: Python, Jupyter, XGBoost, scikit-learn, pandas, NumPy, matplotlib

## Repository Structure

```text
code/
  notebooks/
    current/              Main training, evaluation, and inference notebook
    legacy/               Earlier notebook versions retained for comparison

data/
  current_dataset/        Main dataset used by the active workflow
  training_archive/       Earlier training dataset and manifest
  prediction_examples/    Example forecast input/output CSV files
  raw_reference_datasets/ Older raw/reference datasets retained for context

models/
  current_v7/             Current trained model files and metadata
  legacy_archive/         Older trained models retained for comparison

results/
  analysis_figures/       Exported project figures
  metrics_and_audits/     Metrics JSON and audit CSV files
```

## Main Files

- Notebook: `code/notebooks/current/solar_v7_main_training_and_inference.ipynb`
- Dataset: `data/current_dataset/bycodex_realistic_43_624kw_vit_chennai_2021_2025_5min.csv`
- Model metadata: `models/current_v7/v7_metadata.json`
- Trained models:
  - `models/current_v7/kt_model_v7.pkl`
  - `models/current_v7/power_model_v7.pkl`
  - `models/current_v7/sensor_model_v7.pkl`
- Evaluation summary: `results/metrics_and_audits/metrics_revision_2026-05-23.json`
- Metrics audit: `results/metrics_and_audits/metrics_audit_2026-05-23.csv`

## Data Snapshot

| Item | Value |
| --- | --- |
| Time span | 2021-01-01 to 2025-12-31 |
| Total rows | 525,888 |
| Sampling cadence | 5 minutes |
| Plant capacity | 43.624 kW |
| Test split start | 2024-12-28 |
| Daylight evaluation rows | 52,731 |
| Duplicate timestamps | 0 |
| Cadence gaps | 0 |
| Missing values in core columns | 0 |

## Result Snapshot

| Configuration | MAE (kW) | RMSE (kW) | nRMSE (%) | R2 |
| --- | ---: | ---: | ---: | ---: |
| Proposed two-stage model | 1.9634 | 2.8251 | 6.4758 | 0.9460 |
| Single-stage XGBoost | 2.1674 | 3.0382 | 6.9643 | 0.9376 |
| Two-stage, total cloud only | 1.9865 | 2.8490 | 6.5307 | 0.9451 |
| Previous-day same-time baseline | 3.6101 | 5.4613 | 12.5187 | 0.7984 |
| Sensor-assisted upper bound | 0.3868 | 0.5228 | 1.1985 | 0.9982 |

The previous-day same-time baseline is the more useful operational comparison in this package. The 5-minute last-value persistence baseline exists in the audit files as a strong sensor-driven nowcast reference rather than a clean weather-input forecasting baseline.

## What the Results Show

| Observation | Takeaway |
| --- | --- |
| Two-stage workflow vs single-stage model | The physics-guided intermediate step improves RMSE from 3.0382 kW to 2.8251 kW. |
| Two-stage workflow vs previous-day baseline | The learned model clearly outperforms a simple historical baseline on the same evaluation window. |
| Cloud-layer information | Layered cloud inputs perform slightly better than collapsing cloud effects into total cloud cover alone. |
| Sensor-assisted path | This gives a practical upper-bound reference when stronger live sensor support is available. |

## Included Analysis Artifacts

- Predicted-vs-actual plots
- Residual histogram
- Diurnal error profile
- Monthly spread and cumulative-energy plots
- Weather-regime diagnostics
- Ramp-rate diagnostics
- Duration-curve analysis
- Worst-error-day visualization
- Workflow and evaluation diagrams

These are stored under `results/analysis_figures/`.

## Quick Start

```bash
git clone https://github.com/brinesolution/solar-pv-forecasting.git
cd solar-pv-forecasting
python -m venv .venv
```

Activate the environment:

```bash
# Windows PowerShell
.\.venv\Scripts\Activate.ps1

# macOS/Linux
source .venv/bin/activate
```

Install dependencies and open the notebook:

```bash
pip install -r requirements.txt
jupyter notebook code/notebooks/current/solar_v7_main_training_and_inference.ipynb
```

## Notes

This is a research project repository, not a production forecasting service. The included forecast examples demonstrate the inference workflow, but real deployment would still require a reliable weather-input pipeline, operational monitoring, and fresh validation on the target site.

The trained model files are Python pickle artifacts. Only load them in a trusted environment.

## Author

Mayank Lohani  
Bachelor of Technology in Computer Science and Engineering with specialization in Artificial Intelligence and Machine Learning  
School of Computer Science and Engineering, Vellore Institute of Technology, Chennai, India
