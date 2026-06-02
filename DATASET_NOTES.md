# Dataset Notes

## Active Dataset

The main working dataset in this repository is:

```text
data/current_dataset/bycodex_realistic_43_624kw_vit_chennai_2021_2025_5min.csv
```

It uses the following core schema:

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

This is the dataset used by the active notebook for training, validation, testing, figure generation, and forecast-CSV inference examples.

## Training Archive

`data/training_archive/` contains an earlier training dataset and its manifest. Those files are kept for traceability and comparison with the current working setup.

## Raw Reference Datasets

`data/raw_reference_datasets/` contains older datasets collected during project exploration. They are useful as background material, but they are not the final cleaned inputs used by the active workflow. Some of these files may have partial time coverage, differing schemas, or quality issues typical of early-stage data collection.

## Prediction Examples

`data/prediction_examples/` contains example input and output CSV files used to demonstrate the inference flow. These examples show how the forecasting pipeline can be run on structured external input data.

## File Size

The current package keeps all included files below GitHub's 100 MB single-file limit. If future versions outgrow that limit, the data should be moved to Git LFS or to a research-data host such as Zenodo, Figshare, OSF, or an institutional repository.
