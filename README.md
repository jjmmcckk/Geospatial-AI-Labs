# Geospatial AI Labs

Graduate coursework projects in geospatial AI (University of Georgia), cleaned up, fixed
and documented. Each folder has a runnable notebook and a README with results.

| Lab | Topic | Tools | Key result |
|---|---|---|---|
| [Lab 1](lab1-spatial-regression) | Spatial deep learning regression on GIS point data | GeoPandas, TensorFlow/Keras, scikit-learn | Test RMSE $47,915, 20% below a linear baseline |
| [Lab 2](lab2-aerial-image-classification) | Aerial image land use classification, CNN vs transfer learning | PyTorch, torchvision, Inception v3 | 93.3% test accuracy with transfer learning vs 72.1% for a small CNN |
| [Lab 3](lab3-lstm-precipitation-forecasting) | LSTM time series forecasting of precipitation | PyTorch, scikit-learn | MAE 26.6 mm vs 27.5 mm seasonal baseline |
| [Lab 4](lab4-space2vec-optuna) | Space2Vec location encoding with Optuna tuning | PyTorch, Optuna, GeoPandas | Encoder cuts test RMSE 20% vs raw coordinates |

All notebooks run in Google Colab and are committed with their outputs from a full run
on the course data. Each lab's README has an **Open in Colab** button, and
`requirements.txt` lists the package versions the outputs were produced with. Datasets are not included in this repository; each README
explains where to get them.

**Author:** Jordan McKenzie, Transport Canada Advanced RPAS Pilot and Flight Reviewer,
B.Sc. Computer Science, geospatial and drone data work since 2019.
