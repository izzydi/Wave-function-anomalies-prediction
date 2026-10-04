# Wave-Function Anomaly Detection

An applied scientific machine-learning project for high-dimensional wave-function data, combining **training-only preprocessing, H2O autoencoder representation learning and XGBoost classification**.

## Primary workflow

[`wave_function_anomaly_detection.Rmd`](wave_function_anomaly_detection.Rmd) is the audited source. It uses project-relative data paths, creates a stratified hold-out set before learned preprocessing, fits preprocessing and representation learning using training data only, selects H2O predictors by name rather than fragile column positions, and reuses the trained pipeline for optional external validation.

## Repository structure

- [`wave_function_anomaly_detection.Rmd`](wave_function_anomaly_detection.Rmd) — audited R Markdown workflow.
- [`data/README.md`](data/README.md) — expected source/validation data layout and provenance limitations.
- [`R-packages.txt`](R-packages.txt) — direct package dependencies.
- [`archive/legacy_wave_function_exploration.Rmd`](archive/legacy_wave_function_exploration.Rmd) — original exploratory source retained for transparency.

The old rendered HTML was removed from the current tree because it no longer represented the audited source. Historical versions remain available through Git history.

## Validation design

The hold-out test set is untouched while preprocessing and representation learning are fitted on the training partition. XGBoost cross-validation tunes a classifier on a **fixed representation learned from the training partition**. Because the autoencoder is not re-trained inside each XGBoost fold, those resamples are used for classifier hyperparameter selection rather than reported as an unbiased end-to-end performance estimate. The untouched held-out test set is the primary evaluation set.

Optional validation datasets are transformed using the already-fitted recipe and autoencoder and are not used to refit the pipeline.

## Methods and tools

The project uses `tidymodels`, `data.table`, H2O deep-learning autoencoders, XGBoost and `caret`. The current bottleneck is four-dimensional, making the learned representation compact enough for downstream classification and inspection.

## Data

Raw data are not committed and the historical source materials do not provide a stable public source/version/checksum. See [`data/README.md`](data/README.md) for the exact expected layout and the reproducibility limitation.

## Scope

This is a scientific machine-learning portfolio project. It demonstrates explicit train/test boundaries and train-derived representation learning; it is not a deployed production inference system.
