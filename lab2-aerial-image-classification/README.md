# Lab 2: Aerial Image Land Use Classification

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jjmmcckk/Geospatial-AI-Labs/blob/main/lab2-aerial-image-classification/lab2_aerial_image_classification.ipynb)

Classifies UC Merced aerial orthoimagery (21 land use classes, 2,100 tiles) with
PyTorch, comparing a small CNN trained from scratch against transfer learning from an
ImageNet pretrained Inception v3.

**Why it matters for drone work:** the same approach can classify assets, surface types
or site conditions in drone orthomosaics.

**Skills shown:** PyTorch, convolutional networks, data augmentation, transfer learning,
train/test evaluation, GPU training.

## Fixes made to the original notebook
- Added missing imports (`numpy`, `torch.nn.functional`).
- Replaced an augmented loader that silently overwrote the split and trained on the test
  images with one fixed 80/20 split. The training set is the original images concatenated
  with an augmented copy (four augmentations), as the lab specifies; test images are never
  augmented.
- Added the 3 x 3 preview of training images the lab asks for.
- Inception v3 now gets the 299 x 299 normalised inputs it requires (it fails on 96 px).
- Added the missing Inception training loop, including its auxiliary classifier output.
- Added test accuracy for both models and a comparison chart, plus GPU support and a seed.

## Run it
Open in Google Colab, set the runtime to GPU, and run all cells. The first cell downloads
the dataset.

## Results
Test set: 420 images (20%), never augmented and never used in training. Training set:
1,680 original images plus an augmented copy (3,360 per epoch).

| Model | Test accuracy |
|---|---|
| Simple CNN (10 epochs, 96 x 96 px) | 72.1% |
| **Inception v3 transfer learning (5 epochs, pretrained layers frozen)** | **93.3%** |

Random guessing would score about 5% across 21 classes. Transfer learning adds 21 points
of accuracy in half the epochs, training only the new classification layers, because the
ImageNet pretrained network already recognises edges, textures and shapes. The image
preview and the training loss chart are in the notebook outputs.
