# DCGAN — Face Image Synthesis

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/kr1347/GAN-Model/blob/main/GAN_Model.ipynb)

Deep Convolutional Generative Adversarial Network (DCGAN) trained on VGGFace2 to synthesize photorealistic human face images from random latent vectors.

## Architecture

| Component | Design |
|-----------|--------|
| Generator | 5-layer transposed convolution, BatchNorm, ReLU, Tanh output |
| Discriminator | 5-layer convolution, spectral normalization, LeakyReLU |
| Latent dim | z = 100 |
| Image size | 64×64 RGB |

Spectral normalization on the discriminator stabilizes training and prevents mode collapse (Miyato et al., 2018).

## Dataset

**VGGFace2** — 25,000 face images sampled from the full dataset, resized and center-cropped to 64×64.

## Training

- Optimizer: Adam (lr=1e-4, β₁=0.5, β₂=0.999) for both generator and discriminator
- Loss: Binary Cross-Entropy
- Epochs: 100 with checkpoint resumption
- Hardware: Google Colab GPU

## Results

Generated samples after 100 epochs show coherent facial structure with varied identity, lighting, and pose. Checkpoint resumption allows multi-session training without losing progress.

## Usage

Open the notebook in Colab and run all cells. Checkpoints are saved to Google Drive every epoch.

## References

- Radford, A. et al. (2015). Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks. *arXiv:1511.06434*
- Miyato, T. et al. (2018). Spectral Normalization for Generative Adversarial Networks. *ICLR 2018*
- Cao, Q. et al. (2018). VGGFace2: A dataset for recognising faces across pose and age. *FG 2018*

