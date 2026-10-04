# Legacy analysis

`legacy_wave_function_exploration.Rmd` preserves the original exploratory workflow.

It is not the recommended reproducible implementation because it contains machine-specific Windows paths, repeatedly fits preprocessing objects, and refers to predictors by fixed column positions even after feature-removal steps can change the schema.

The current audited source is [`../wave_function_anomaly_detection.Rmd`](../wave_function_anomaly_detection.Rmd). It uses project-relative paths, a single training-fitted preprocessing recipe, predictor names instead of fragile numeric positions, an untouched hold-out set, and optional external validation that reuses the trained pipeline.

The root HTML file is retained as a historical rendered artifact and may not reflect the current audited R Markdown source.
