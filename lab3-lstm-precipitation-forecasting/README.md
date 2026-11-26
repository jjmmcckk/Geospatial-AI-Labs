# Lab 3: LSTM Precipitation Forecasting

Forecasts next month precipitation in Hawaii (1939 to 2024) from the previous 12 months
with a stacked LSTM in PyTorch, and compares it with a naive baseline.

**Skills shown:** time series preparation, sliding windows, chronological validation,
PyTorch LSTM, evaluation in real units.

## Fixes made to the original notebook
- Added missing imports and a single, consistent data path.
- Fixed a shape mismatch: targets held 12 values while the model predicted 1. Each sample
  now predicts the next month.
- Replaced a shuffled random split with a chronological split, and fit the scaler on the
  training period only, to avoid leaking future information.
- Reported error in millimetres and added a naive baseline for context.

## Run it
Open in Google Colab, upload `HW_precipitation_1939_2024.csv`, and run all cells.

## Results
| Model | Test MAE (mm) |
|---|---|
| LSTM | _fill in_ |
| Naive baseline | _fill in_ |
