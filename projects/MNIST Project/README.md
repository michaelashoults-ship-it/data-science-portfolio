# MNIST Project

## Overview

This project, worked on with a group, was for MA 323: Intro to Data Science. It analyzes the MNIST handwritten digit dataset using geometric distance metrics, optimal transport methods, and linear algebra techniques. The goal is to study the structure of high-dimensional image data and understand how different mathematical tools capture similarity between images.

The analysis includes:
- Pairwise distance matrices under multiple norms
- Wasserstein (W1) distance using optimal transport
- Low-rank approximation using Singular Value Decomposition (SVD)

---

## Dataset

- MNIST dataset from `sklearn.datasets.fetch_openml`
- 70,000 total images of handwritten digits (0–9)
- Each image is 28 × 28 pixels
- A random subset of 5,000 images was selected
- Each image is flattened into a vector in \( \mathbb{R}^{784} \)

---

## 1. Distance Analysis

### Method

Each image is treated as a vector in 784-dimensional space. Pairwise distances were computed using:

- ℓ₁ (Manhattan distance)
- ℓ₂ (Euclidean distance)
- ℓ∞ (Chebyshev distance)

Distance matrices were visualized using heatmaps. Images were sorted by label to reveal block structure.

---

### Key Observations

- Strong block structure appears when images are grouped by digit class
- ℓ₂ and ℓ₁ norms show clear separation between digit clusters
- ℓ∞ distance is less informative due to sensitivity to pixel extremes
- Within-class distances are significantly smaller than between-class distances

---

## 2. Wasserstein Distance (Optimal Transport)

### Method

Each image was converted into a probability distribution by thresholding pixel intensity values.

- Pixels above threshold (80) were treated as mass
- Images were normalized to sum to 1
- Pairwise Wasserstein-1 distances were computed using the POT library (`ot.emd2`)
- Computation was parallelized due to high cost

---

### Key Observations

- Wasserstein distance captures geometric structure of digits
- More robust to small shifts in handwriting compared to ℓp norms
- Produces clearer structure in clustering of digit classes
- Generally lower and more stable distance values than ℓ₁ / ℓ₂

---

## 3. Low-Rank Approximation (SVD)

### Method

Images of a selected digit class (e.g., digit “1”) were:

- Vectorized into \( \mathbb{R}^{784} \)
- Stacked into a matrix \( A \in \mathbb{R}^{784 \times m} \)
- Decomposed using Singular Value Decomposition:
\[
A = U \Sigma V^T
\]

A low-rank approximation was constructed by truncating singular values.

---

### Key Results

- The digit class exhibits strong low-dimensional structure
- The smallest rank achieving <10% reconstruction error was:
  - **k ≈ 91 (for digit 1)**
- This suggests handwritten digits lie on a low-dimensional manifold within 784D space

---

### Visualization Results

- Reconstruction from rank-k approximation closely matches original images
- Higher singular modes capture stroke variation and writing style differences
- Top singular vectors resemble “eigendigits”

---

## Key Insights

- Different distance metrics capture different notions of similarity:
  - ℓ₂ / ℓ₁ → pixel-wise differences
  - ℓ∞ → extreme pixel sensitivity
  - Wasserstein → geometric structure
- Optimal transport provides a more meaningful similarity metric for images
- SVD reveals that digit classes are highly compressible and structured

---

## Tools Used

- Python
- NumPy
- Matplotlib
- SciPy
- scikit-learn (MNIST loader)
- POT (Python Optimal Transport)
- Joblib (parallel computation)

---

## Key Concepts

- High-dimensional geometry
- Distance metrics (ℓ₁, ℓ₂, ℓ∞)
- Optimal transport (Wasserstein distance)
- Image as probability distribution
- Singular Value Decomposition (SVD)
- Low-rank approximation
- Manifold structure in data

---

## Authors

- Michaela Shoults
- Cole Davis
- Lauren Hayes
- Rachel Dusek
