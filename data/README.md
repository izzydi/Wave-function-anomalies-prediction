# Data directory

The raw wave-function datasets are intentionally not committed to this repository.

The original R Markdown analysis was created with machine-specific absolute Windows paths. For a portable local setup, place the source files in this directory and update the import paths in the analysis to use project-relative paths.

Suggested filenames:

- `wave_functions.csv` — primary training source.
- `shock_1.csv` — external validation set 1.
- `shock_2.csv` — external validation set 2.
- `gaussian.csv` — Gaussian validation set.
- `shock_4.csv` — external validation set 4.

Raw data files are excluded by `.gitignore` so large or non-public datasets are not accidentally committed.
