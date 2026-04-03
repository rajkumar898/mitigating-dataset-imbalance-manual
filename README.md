# Mitigating Dataset Imbalance for Solar Panel Dust Detection using Stable Diffusion and SMOTE

## Overview

This project addresses the problem of **dataset imbalance** in solar panel dust detection using a hybrid approach that combines **SMOTE** (Synthetic Minority Over-sampling Technique) and **Stable Diffusion XL**. The original dataset (**SolNET**) contains an unequal number of clean and dirty solar panel images, which can negatively impact model performance.

## Approach

1. **SMOTE** – Applied to synthetically balance the dataset in feature space.
2. **Stable Diffusion XL** – Used to generate realistic faulty solar panel images, increasing data diversity and improving representation of the minority class.
3. **Image Quality Validation** – Generated images are validated using **FID/KID** (Fréchet/Kernel Inception Distance) and **perceptual hashing (pHash)**.
4. **VGG16 Transfer Learning** – A deep learning model is trained on the merged real + synthetic dataset with data augmentation.
5. **10-Fold Stratified Cross-Validation** – Model is evaluated rigorously with performance metrics including accuracy, precision, recall, and F1-score.

## Dataset

The **SolNET** dataset contains labeled images of solar panels in two classes:
- `clean` – Solar panels without dust/dirt
- `dirty` – Solar panels with dust/dirt contamination

> **Download:** Place your dataset in the `data/` directory following the structure below, or update the `DATASET_PATH` variable in the notebook.

```
data/
├── clean/
│   ├── image_001.jpg
│   ├── image_002.jpg
│   └── ...
└── dirty/
    ├── image_001.jpg
    ├── image_002.jpg
    └── ...
```

## Project Structure

```
.
├── README.md
├── requirements.txt
├── mitigating_dataset_imbalance.ipynb   ← Main notebook
└── data/
    ├── clean/
    └── dirty/
```

## Setup

### 1. Install Dependencies

```bash
pip install -r requirements.txt
```

### 2. Launch Jupyter

```bash
jupyter notebook mitigating_dataset_imbalance.ipynb
```

### 3. Run Cells in Order

The notebook is organized into clearly numbered sections. Run each section top-to-bottom. GPU acceleration is strongly recommended for Stable Diffusion XL inference.

## Requirements

- Python ≥ 3.9
- CUDA-capable GPU (recommended for Stable Diffusion XL)
- ~10 GB free disk space for model weights

## Key Libraries

| Library | Purpose |
|---|---|
| `tensorflow` / `keras` | VGG16 transfer learning |
| `imbalanced-learn` | SMOTE oversampling |
| `diffusers` | Stable Diffusion XL pipeline |
| `torch` | PyTorch backend for diffusion |
| `scikit-learn` | Cross-validation, metrics |
| `clean-fid` | FID / KID computation |
| `ImageHash` | Perceptual hashing (pHash) |
| `matplotlib` / `seaborn` | Visualisation |

## Results Summary

The combination of diffusion-based image generation and traditional resampling techniques significantly improves classification performance, providing a robust solution for handling imbalanced datasets in real-world solar panel monitoring applications.

## Citation

If you use this work, please cite:

```
@article{solnet2024,
  title   = {Mitigating Dataset Imbalance for Solar Panel Dust Detection
             using Stable Diffusion and SMOTE},
  year    = {2024}
}
```
