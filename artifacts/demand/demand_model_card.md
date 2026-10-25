# Model Card — taxi-demand-forecaster

_Generated 2026-10-22 06:40 UTC_

## Overview
Predicts the number of taxi pickups for a given zone and hour (demand forecasting).

- **Problem:** demand
- **Best algorithm:** xgboost
- **Registry name:** `taxi-demand-forecaster`
- **Training data window:** 2024-01
- **Training rows:** 116,582

## Test-set performance

| Metric | Test | Validation |
|--------|------|------------|
| RMSE | 8.8504 | 8.1382 |
| MAE | 2.5514 | 2.5007 |
| MAPE | 40.1314 | 43.7253 |
| R2 | 0.9697 | 0.9647 |

## Top feature drivers (mean |SHAP|)

1. `lag_1` — 10.1107
2. `lag_168` — 7.2450
3. `lag_24` — 4.5143
4. `rolling_mean_3` — 1.2912
5. `hour_cos` — 0.7558
6. `lag_2` — 0.6068
7. `rolling_mean_168` — 0.3935
8. `rolling_std_3` — 0.3502
9. `lag_3` — 0.3328
10. `hour` — 0.3046

## Hyperparameters

```json
{
  "n_estimators": 500,
  "max_depth": 8,
  "learning_rate": 0.036579786528836776,
  "subsample": 0.8947028606125237,
  "colsample_bytree": 0.6005560195979014,
  "min_child_weight": 8,
  "reg_lambda": 0.003507051809936812
}
```

## Limitations

- Trained on a single month of NYC TLC Yellow Taxi data; seasonal effects beyond the training window are not captured.
- Lag/rolling features require recent history — cold-start zones/hours are less reliable.
- Only Yellow Taxi pickups are modelled (no green taxi / FHV).
