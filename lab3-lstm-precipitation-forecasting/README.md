# Lab 3: LSTM Precipitation Forecasting

Forecasts next month precipitation at Honolulu Airport, Hawaii (NOAA NCEI, 1940 to 2024)
from the previous 12 months with a stacked LSTM in PyTorch, and compares it with seasonal
and naive baselines.

**Skills shown:** time series preparation, sliding windows, chronological validation,
PyTorch LSTM, evaluation in real units.

## Fixes made to the original notebook
- Added missing imports and a single, consistent data path.
- Fixed a shape mismatch: targets held 12 values while the model predicted 1. Each sample
  now predicts the next month.
- Replaced a shuffled random split with a chronological split, and fit the scaler on the
  training period only, to avoid leaking future information.
- Read the NOAA file as delivered (four header lines, inches, `-99` for missing months):
  converted to millimetres and filled the 8 missing months by linear interpolation.
- Reported error in millimetres and added seasonal and naive baselines for context.

## Run it
Open in Google Colab, upload `HW_precipitation_1939_2024.csv`, and run all cells.

## Results
Test period: June 2007 to February 2024 (201 months), never seen in training.

| Model | Test MAE (mm) |
|---|---|
| **LSTM** | **26.8** |
| Seasonal median (training median for each calendar month) | 27.5 |
| Naive (next month equals this month) | 37.5 |

The LSTM learns the wet winter and dry summer cycle and beats both baselines, but only by
about 3% over the seasonal median. Monthly rainfall at Honolulu is driven by irregular
storms: the forecast plot shows the model tracking the seasonal pattern but not the storm
peaks, which is the expected limit of forecasting from rainfall history alone.
