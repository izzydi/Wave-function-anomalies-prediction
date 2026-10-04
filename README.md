# Wave-Function Anomaly Detection

A scientific machine-learning project focused on identifying anomalous patterns in high-dimensional wave-function data.

## Project overview

The analysis combines statistical preprocessing, representation learning and predictive modelling to study unusual wave-function behaviour. The full workflow is available as R Markdown source and as a rendered HTML report.

## Repository structure

- [`wave_function_anomaly_detection.Rmd`](wave_function_anomaly_detection.Rmd) — source analysis.
- [`wave_function_anomaly_detection.html`](wave_function_anomaly_detection.html) — rendered report.
- [`data/README.md`](data/README.md) — expected local dataset layout.
- [`.gitignore`](.gitignore) — prevents raw CSV data and local R artifacts from being committed accidentally.

## Methods

The analysis includes:

- exploratory data analysis,
- recipe-based preprocessing,
- correlation and linear-combination filtering,
- Yeo-Johnson transformation and normalization,
- H2O autoencoders for learned representations,
- XGBoost classification,
- cross-validation and hyperparameter tuning,
- external validation datasets.

## Reproducibility note

The original 2022 R Markdown workflow contains machine-specific absolute Windows paths from the environment in which it was developed. The original analysis is preserved for transparency. For a portable setup, use the filenames documented in `data/README.md` and replace those absolute imports with project-relative `data/...` paths before running the report.

## Viewing the report

Download `wave_function_anomaly_detection.html` and open it locally in a browser, or use a compatible HTML preview service.

## Scope

This is an experimental scientific machine-learning portfolio project. It should be interpreted as an analytical demonstration rather than a validated physics simulation or production anomaly-detection system.
