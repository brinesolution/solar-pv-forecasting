# Solar PV Power Forecasting with Physics-Guided XGBoost

This is a research-oriented solar forecasting project for predicting 5-minute-grid photovoltaic power output from plant and weather data. The work uses a two-stage XGBoost pipeline: the first stage estimates a clearness-index-like irradiance behavior, and the second stage predicts PV power using weather inputs, solar-position features, cloud-cover variables, and learned plant behavior.

The project was built around a 43.624 kW solar PV plant case study at VIT Chennai, Tamil Nadu, India. It is intended to be readable as a standalone public project as well as a supporting repository for a research manuscript.

## What This Project Contains

This repository includes the main notebook, the dataset used for the study, trained model artifacts, prediction examples, exported figures, metrics tables, and the current manuscript draft. Internal helper scripts and the local Python virtual environment are intentionally not included, so the repository stays focused on the artifacts needed to understand and inspect the work.

## Project Highlights

- 5-minute-grid solar PV power prediction for a 43.624 kW plant case study
- Physics-guided feature engineering using solar geometry, clear-sky behavior, irradiance proxies, and plant-capacity constraints
- Two-stage XGBoost design:
  - Stage 1: clearness-index / irradiance behavior model
  - Stage 2: PV power prediction model
- Chronological train, validation, and test workflow
- Notebook-based figures and metrics for paper-style analysis
- Forecast-CSV inference examples for demonstrating how the trained pipeline can be used with external weather inputs
- Current and older project artifacts retained for traceability

## Repository Structure

```text
code/
  notebooks/
    current/              Main training, evaluation, and inference notebook
    legacy/               Earlier notebooks retained for development history

data/
  current_dataset/        Main dataset used by the active notebook
  training_archive/       Earlier training dataset and manifest
  prediction_examples/    Example forecast input/output CSV files
  raw_reference_datasets/ Older raw/reference datasets retained for context

models/
  current_v7/             Current trained model files and metadata
  legacy_archive/         Older trained models retained for comparison

results/
  paper_figures/          Figures exported from the notebook workflow
  latex_figures/          Figures packaged with the manuscript draft
  tables_and_metrics/     Metrics, tables, and audit files

manuscript/
  compiled_pdf/           Current compiled paper draft
  latex_source/           LaTeX source used for the manuscript

docs/
  project_context/        Project context and asset inventory snapshots
```

## Main Files

- Notebook: `code/notebooks/current/solar_v7_main_training_and_inference.ipynb`
- Dataset: `data/current_dataset/bycodex_realistic_43_624kw_vit_chennai_2021_2025_5min.csv`
- Model metadata: `models/current_v7/v7_metadata.json`
- Trained models:
  - `models/current_v7/kt_model_v7.pkl`
  - `models/current_v7/power_model_v7.pkl`
  - `models/current_v7/sensor_model_v7.pkl`
- Metrics audit: `results/tables_and_metrics/metrics_audit_2026-05-23.csv`
- Manuscript draft: `manuscript/compiled_pdf/solar_pv_forecasting_ieee_access_draft.pdf`

## Quick Start

Clone the repository and create a Python environment:

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

Install the required packages:

```bash
pip install -r requirements.txt
```

Open the notebook:

```bash
jupyter notebook code/notebooks/current/solar_v7_main_training_and_inference.ipynb
```

## Data Columns

The main dataset uses the following core schema:

```text
time
irradiance
power
theoretical_power
temp
humidity
wind_speed
precipitation
cloud_cover
cloud_cover_low
cloud_cover_mid
cloud_cover_high
```

See `DATASET_NOTES.md` for details about the active dataset, archived training files, prediction examples, and raw reference datasets.

## Results and Figures

The main results are available in:

- `results/paper_figures/`
- `results/tables_and_metrics/`
- `manuscript/compiled_pdf/solar_pv_forecasting_ieee_access_draft.pdf`

The metrics and figures are included so the notebook outputs, manuscript tables, and paper plots can be inspected without rebuilding the whole project from scratch.

## Important Notes

The model files are stored as Python pickle artifacts. Only load them in a trusted environment.

This repository is a research project, not a production forecasting service. The forecast-CSV examples demonstrate the inference workflow, but operational use would require a reliable weather-input pipeline and fresh validation on the target deployment site.

No local virtual environment, cache folder, or internal helper script folder is included.

## Citation

If you use this repository, cite the related manuscript and this GitHub repository. A draft citation file is provided in `CITATION.cff`; update it with the final DOI or archived repository DOI when available.

## Author

Mayank Lohani  
Bachelor of Technology in Computer Science and Engineering with specialization in Artificial Intelligence and Machine Learning  
School of Computer Science and Engineering, Vellore Institute of Technology, Chennai, India

## License

No license has been selected yet. Until a license is added, please treat the repository as publicly visible research material, not as freely reusable software.
