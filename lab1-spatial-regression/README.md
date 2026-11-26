# Lab 1: Spatial Deep Learning Regression

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
Open in Google Colab, upload `California_housing.shp` with its `.shx`, `.dbf` and `.prj`
files, and run all cells.

## Results
Test RMSE: _fill in after running_
