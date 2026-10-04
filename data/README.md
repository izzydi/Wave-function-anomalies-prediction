# Data directory

The raw wave-function datasets are not committed to this repository.

The audited workflow already uses project-relative paths. Expected layout:

```text
data/
├── wave_functions.csv
└── validation/          # optional
    ├── shock_1.csv
    ├── shock_2.csv
    ├── gaussian.csv
    └── shock_4.csv
```

The primary dataset must contain at least 113 columns; the first 112 are predictors and column 113 is the target. Validation files use the same schema.

The archived 2022 source shows that the original primary file was read from a machine-specific local path and does not provide a stable public source/version/checksum. The cleaned repository therefore does **not** claim that the raw data can be reconstructed from a public download. Use the exact original data where available and record its provenance/checksum for any reproduced metrics.

Raw data files remain excluded by `.gitignore` so large or non-public datasets are not accidentally committed.
