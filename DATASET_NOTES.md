# Dataset Notes

## Active Dataset

The active dataset for the manuscript and notebook workflow is:

```text
data/current_dataset/bycodex_realistic_43_624kw_vit_chennai_2021_2025_5min.csv
```

It follows the project modeling schema:

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

The active notebook uses this dataset for the two-stage XGBoost workflow, train/validation/test evaluation, figures, tables, and forecast-CSV demonstration.

## Training Archive

`data/training_archive/` contains the earlier v7 training dataset and associated manifest retained for traceability. These files are included so readers can see the historical project artifacts that existed before the current active dataset and manuscript package were finalized.

## Raw Reference Datasets

`data/raw_reference_datasets/` contains older/raw datasets gathered during project exploration. These files may have incomplete time windows, missing values, inconsistent schemas, duplicated files, or faulty/corrupted readings. They are included for auditability and background context, not as the final cleaned training input.

## Prediction Examples

`data/prediction_examples/` contains example forecast-CSV input and output files used to demonstrate the inference path. Demonstration output files are not validation metrics unless matched measured PV output is available for the same time window.

## File-Size Note

The dataset files included here are intended to remain under GitHub's single-file upload limit. If a future version grows beyond that limit, use Git LFS, Zenodo, Figshare, OSF, or an institutional repository, and cite the permanent DOI in the manuscript appendix.
