# Lab 4: Location Encoding with Space2Vec and Optuna

Encodes coordinates with a multi scale Space2Vec style location encoder, combines the
embedding with tabular features in a PyTorch network, and tunes the encoder and network
with Optuna.

**Skills shown:** spatial representation learning, multi scale sinusoidal location
encoding, PyTorch model design, hyperparameter optimisation with Optuna, validation and
test discipline.

## Fixes made to the original notebook
- The Space2Vec repository was cloned after it was imported; the notebook now installs
  dependencies first and includes a built in implementation of the encoder.
- The model's input size ignored the location embedding; it now adds the embedding size.
- The Optuna objective returned an undefined `validation_score` without training anything.
  It now builds, trains and scores a model on a validation set for every trial.
- Constrained `min_radius` below `max_radius` (the original search could exceed it).
- Added a held out test score using the best parameters, and an ablation that swaps the
  encoder for raw coordinates to show what the encoder itself contributes.

## Run it
Open in Google Colab, upload the California housing shapefile from Lab 1, and run all
cells. A GPU speeds up the search.

## Results
30 Optuna trials, each trained and scored on a validation set (best validation RMSE
$40,479). The tuned network was then trained with the Space2Vec encoder and, as an
ablation, with the same layers fed raw coordinates instead, over 3 seeds each, and scored
on the held out test set.

| Location input | Test RMSE (mean of 3 seeds) | Std |
|---|---|---|
| **Space2Vec encoder** | **$40,195** | $142 |
| Raw coordinates | $50,331 | $132 |

The encoder lowers test RMSE by 20% compared with raw coordinates, far more than the
seed to seed variation, and is about 16% below the Lab 1 network ($47,915) on the same
3,715 test blocks.

Best parameters: embedding size 64, 16 frequencies, min radius 0.0019, 2 hidden layers of
64 units, dropout 0.12, learning rate 0.00072.
