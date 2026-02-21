
# Learning Probability Density Function using GAN

## Overview
This project learns the probability density function (PDF) of a transformed random variable using a Generative Adversarial Network (GAN).  
No parametric distribution (Gaussian, etc.) is assumed — the model learns directly from data samples.

---

## Dataset
- Source: India Air Quality Dataset (Kaggle)
- Feature used: NO₂ concentration

---

## Step 1: Transformation
For roll number **102303563**:

a_r = 1.5  
b_r = 1.2  

Transformation applied:
z = x + 1.5 sin(1.2x)

---

## Step 2: GAN Model
Generator:
- Input: 1D Gaussian noise
- Layers: 1 → 64 → 32 → 1
- Activation: LeakyReLU

Discriminator:
- Input: 1D sample
- Layers: 1 → 64 → 32 → 1
- Output: Real/Fake probability

Training:
- Loss: Binary Cross Entropy
- Optimizer: Adam
- Epochs: 2500
- Batch Size: 128

---

## Step 3: PDF Estimation
- Generate large samples from trained generator
- Apply Kernel Density Estimation (KDE)
- Compare with histogram of real transformed data

---

## Observations
- GAN captures main modes of distribution
- Training remains stable
- Estimated PDF closely matches real distribution

---

## Conclusion
GAN successfully learns an unknown probability distribution using only sample data.
