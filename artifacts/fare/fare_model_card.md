# Model Card — taxi-fare-predictor

_Generated 2026-10-22 06:22 UTC_

## Overview
Predicts the fare amount for a single taxi trip from its distance, zones, passenger count and calendar context (fare prediction).

- **Problem:** fare
- **Best algorithm:** lightgbm
- **Registry name:** `taxi-fare-predictor`
- **Training data window:** 2024-01
- **Training rows:** 2,181,879

## Test-set performance

| Metric | Test | Validation |
|--------|------|------------|
| RMSE | 3.4486 | 3.3495 |
| MAE | 0.7979 | 0.7485 |
| MAPE | 8.7346 | 14.8328 |
| R2 | 0.9556 | 0.9560 |

## Top feature drivers (mean |SHAP|)

1. `trip_distance` — 8.5178
2. `trip_duration_min` — 3.8730
3. `DOLocationID` — 0.4283
4. `PULocationID` — 0.1865
5. `passenger_count` — 0.1126
6. `hour_cos` — 0.0486
7. `hour` — 0.0382
8. `hour_sin` — 0.0265
9. `day_of_week` — 0.0165
10. `dow_sin` — 0.0150

## Hyperparameters

```json
{
  "n_estimators": 400,
  "num_leaves": 119,
  "max_depth": 8,
  "learning_rate": 0.11911416973807151,
  "subsample": 0.61044924391467,
  "colsample_bytree": 0.9719206486280353,
  "min_child_samples": 76,
  "reg_lambda": 3.3236656153632627
}
```

## Limitations

- Trained on a single month of NYC TLC Yellow Taxi data; tariff changes or surge conditions outside the window are not represented.
- Extreme fares are filtered during cleaning, so very long/expensive trips may be under-predicted.
- Tolls, tips and surcharges are not part of the modelled fare amount.
