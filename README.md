# Geospatial AI Labs

Graduate coursework projects in geospatial AI (University of Georgia), cleaned up, fixed
and documented. Each folder has a runnable notebook and a README with results.

| Lab | Topic | Tools | Key result |
|---|---|---|---|
| [Lab 1](lab1-spatial-regression) | Spatial deep learning regression on GIS point data | GeoPandas, TensorFlow/Keras, scikit-learn | Test RMSE $47,609 |
| [Lab 2](lab2-aerial-image-classification) | Aerial image land use classification, CNN vs transfer learning | PyTorch, torchvision, Inception v3 | Pending GPU run |
| [Lab 3](lab3-lstm-precipitation-forecasting) | LSTM time series forecasting of precipitation | PyTorch, scikit-learn | MAE 26.8 mm vs 27.5 mm seasonal baseline |
| [Lab 4](lab4-space2vec-optuna) | Space2Vec location encoding with Optuna tuning | PyTorch, Optuna, GeoPandas | Test RMSE $41,101, 14% better than Lab 1 |

All notebooks run in Google Colab. Labs 1, 3 and 4 are committed with their outputs from
a full run on the course data. Datasets are not included in this repository; each README
explains where to get them.

**Author:** Jordan McKenzie, Transport Canada Advanced RPAS Pilot and Flight Reviewer,
B.Sc. Computer Science, geospatial and drone data work since 2019.
