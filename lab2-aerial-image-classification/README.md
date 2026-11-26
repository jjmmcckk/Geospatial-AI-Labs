# Lab 2: Aerial Image Land Use Classification

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
  images with one fixed split, augmented training images and plain test images.
- Inception v3 now gets the 299 x 299 normalised inputs it requires (it fails on 96 px).
- Added the missing Inception training loop, including its auxiliary classifier output.
- Added test accuracy for both models and a comparison chart, plus GPU support and a seed.

## Run it
Open in Google Colab, set the runtime to GPU, and run all cells. The first cell downloads
the dataset.

## Results
Pending: results will be added after the GPU run.
