# Lab 1: Spatial Deep Learning Regression

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jjmmcckk/Geospatial-AI-Labs/blob/main/lab1-spatial-regression/lab1_spatial_regression.ipynb)

Predicts median house value for California census blocks with a 3 layer neural network,
built from a point shapefile.

**Skills shown:** GeoPandas shapefile pipeline, data cleaning, feature engineering from
geometry (latitude and longitude), one hot encoding, scaling, TensorFlow/Keras regression,
evaluation with RMSE.

## Fixes made to the original notebook
- Removed duplicated imports and made the data path configurable.
- Fixed a row misalignment bug: scaled features were rebuilt with a new index and
  concatenated against dummy columns with the original index, scrambling rows.
  Scaling now happens in place on a copy, so every row keeps its target.
- Trained on value in $100k units for stable optimisation, then reported RMSE in dollars.
- Replaced `mean_squared_error(..., squared=False)`, removed in newer scikit-learn.
- Added early stopping and a reproducible seed.

## Run it
Open in Google Colab, upload `california_housing.shp` with its `.shx`, `.dbf` and `.prj`
files, and run all cells.

## Results
Scored on 3,715 held out census blocks (80/20 split of the 18,572 blocks left after
removing capped age and value records), against a linear regression baseline trained on
the same features and split.

| Model | Test RMSE | R² |
|---|---|---|
| **3 layer neural network** | **$47,915** | **0.759** |
| Linear regression baseline | $59,820 | 0.624 |

The neural network lowers RMSE by 20% over the baseline. Early stopping ended training
after 56 epochs; the loss curve and the predicted vs true plot are in the notebook.
