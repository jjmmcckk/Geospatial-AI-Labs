# Lab 4: Location Encoding with Space2Vec and Optuna

Encodes coordinates with a multi scale Space2Vec style location encoder, combines the
embedding with tabular features in a PyTorch network, and tunes the encoder and network
with Optuna.

**Skills shown:** spatial representation learning, multi scale sinusoidal location
encoding, PyTorch model design, hyperparameter optimisation with Optuna, validation and
test discipline.

## Fixes made to the original notebook
- The Space2Vec repository was cloned after it was imported; the notebook now installs
  dependencies first and includes a built in encoder so it always runs.
- The model's input size ignored the location embedding; it now adds the embedding size.
- The Optuna objective returned an undefined `validation_score` without training anything.
  It now builds, trains and scores a model on a validation set for every trial.
- Constrained `min_radius` below `max_radius` (the original search could exceed it).
- Added a held out test score using the best parameters.

## Run it
Open in Google Colab, upload the California housing shapefile from Lab 1, and run all
cells. A GPU speeds up the search.

## Results
- Best validation RMSE: _fill in_
- Test RMSE with tuned parameters: _fill in_
- Best parameters: _fill in_
