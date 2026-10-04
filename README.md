# Wave-Function Anomaly Detection

An applied scientific machine-learning project for high-dimensional wave-function data, combining **training-only preprocessing, H2O autoencoder representation learning and XGBoost classification**.

## Primary workflow

[`wave_function_anomaly_detection.Rmd`](wave_function_anomaly_detection.Rmd) is the audited source. It uses project-relative data paths, creates a stratified hold-out set before learned preprocessing, fits preprocessing and representation learning using training data only, selects H2O predictors by name rather than fragile column positions, and reuses the trained pipeline for optional external validation.

## Repository structure

- [`wave_function_anomaly_detection.Rmd`](wave_function_anomaly_detection.Rmd) — audited R Markdown workflow.
- [`data/README.md`](data/README.md) — expected source/validation data layout and provenance limitations.
- [`R-packages.txt`](R-packages.txt) — version-pinned direct R package dependencies.
- [`.github/workflows/r-ci.yml`](.github/workflows/r-ci.yml) — R 4.6.1 / Java 17 dependency and syntax CI.
- [`archive/legacy_wave_function_exploration.Rmd`](archive/legacy_wave_function_exploration.Rmd) — original exploratory source retained for transparency.

The old rendered HTML was removed from the current tree because it no longer represented the audited source. Historical versions remain available through Git history.

## Validation design

The hold-out test set is untouched while preprocessing and representation learning are fitted on the training partition. The downstream XGBoost classifier uses a **fixed, pre-specified baseline configuration**, rather than tuning hyperparameters with classifier cross-validation on a representation already learned from the complete outer training partition. This removes the earlier validation-boundary mismatch. The untouched held-out test set is the only performance-evaluation set.

Optional validation datasets are transformed using the already-fitted recipe, autoencoder and classifier and are not used to refit any part of the pipeline.

## Reproducibility and CI

The direct R package versions are pinned in [`R-packages.txt`](R-packages.txt). GitHub Actions uses R 4.6.1, Java 17 and `pak` to install those exact direct package versions, then extracts and parses the canonical R Markdown source. Java 17 is within the supported range of the pinned H2O release.

The H2O autoencoder requests reproducible mode with a fixed seed. The downstream XGBoost baseline is also fixed-seed and single-threaded to reduce run-to-run variation.

The raw source data are not publicly reconstructable from the historical project materials, so CI intentionally validates the environment and source syntax rather than pretending to run the unavailable data-dependent workflow.

`R-packages.txt` pins direct dependencies; it is not a complete `renv.lock` for every recursive package dependency.

## Methods and tools

The project uses `tidymodels`, `data.table`, H2O deep-learning autoencoders, XGBoost and `caret`. The current bottleneck is four-dimensional, making the learned representation compact enough for downstream classification and inspection.

## Data

Raw data are not committed and the historical source materials do not provide a stable public source/version/checksum. See [`data/README.md`](data/README.md) for the exact expected layout and the reproducibility limitation.

## Running the analysis

1. Install R 4.6.1 and Java 17.
2. Install `pak` and the pinned direct dependencies:

```r
install.packages("pak")
pak::pkg_install(readLines("R-packages.txt"), upgrade = FALSE)
```

3. Place the source/validation files under `data/` as documented.
4. Run or knit `wave_function_anomaly_detection.Rmd` from top to bottom.

## Scope

This is a scientific machine-learning portfolio project. It demonstrates explicit train/test boundaries, train-derived representation learning and a deliberately fixed downstream baseline; it is not a deployed production inference system.
