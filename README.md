# Wave-Function Anomaly Detection

An applied scientific machine-learning project for high-dimensional wave-function data, combining **training-only preprocessing, H2O autoencoder representation learning and XGBoost classification**.

## Primary workflow

[`wave_function_anomaly_detection.Rmd`](wave_function_anomaly_detection.Rmd) is the audited source. It uses project-relative data paths, creates a stratified hold-out set before learned preprocessing, fits one preprocessing recipe on training data only, selects H2O predictors by name rather than fragile column positions, and reuses the trained pipeline for optional external validation.

## Repository structure

- [`wave_function_anomaly_detection.Rmd`](wave_function_anomaly_detection.Rmd) — audited R Markdown workflow.
- [`data/README.md`](data/README.md) — expected source/validation data layout.
- [`R-packages.txt`](R-packages.txt) — direct package dependencies.
- [`archive/legacy_wave_function_exploration.Rmd`](archive/legacy_wave_function_exploration.Rmd) — original exploratory source retained for transparency.
- [`wave_function_anomaly_detection.html`](wave_function_anomaly_detection.html) — historical rendered report; it may not reflect the current audited source.

## Validation design

The hold-out test set is untouched while preprocessing and representation learning are fitted on the training partition. XGBoost cross-validation tunes a classifier on the fixed train-derived representation; the hold-out test set is therefore the main unbiased evaluation set. Optional validation datasets are transformed using the already-fitted recipe and autoencoder and are not used to refit the pipeline.

## Methods and tools

The project uses `tidymodels`, `data.table`, H2O deep-learning autoencoders, XGBoost and `caret`. The current bottleneck is four-dimensional, making the learned representation compact enough for downstream classification and inspection.

## Data

Raw data are not committed. See [`data/README.md`](data/README.md) for the expected layout.

## Scope

This is a scientific machine-learning portfolio project. It demonstrates reproducible representation learning and anomaly-oriented classification; it is not a deployed production inference system.
