# EN3150 Assignment 03 — Resource-Constrained CNN

This repository contains the shared data pipeline and four model experiments for edge-oriented image classification with the UCI Jute Pest Dataset.

## Contributors

1. FERNANDO G.S.S. — 230179K — fernandogss.23@uom.lk — Computer Science & Engineering
2. HEWAWASAM H.R.L. — 230223R — hewawasamhrl.23@uom.lk — Electrical Engineering
3. BANDARA W.D.T. — 230083K — bandarawdt.23@uom.lk — Electrical Engineering
4. HERATH H.M.D.N.B. — 230240P — herathhmdnb.23@uom.lk — Electrical Engineering

## Dataset

The experiments use the [UCI Jute Pest Dataset](https://archive.ics.uci.edu/dataset/920/jute+pest+dataset) (dataset ID 920, DOI `10.24432/C5289P`). UCI reports 7,235 images across 17 pest classes.

The shared data notebook combines the archive's original folders and creates one reproducible stratified split used by every model:

- Input: 64 × 64 RGB images
- Classes: 17
- Split: 70% training, 15% validation, 15% test
- Random seed: 42
- Batch size: 64

The exact file assignments and class ordering are stored in a shared split manifest. This prevents the model notebooks from evaluating on different samples.

## Notebooks

| Notebook | Owner | Purpose |
| --- | --- | --- |
| [`00_shared_data_and_final_comparison.ipynb`](notebooks/00_shared_data_and_final_comparison.ipynb) | Sahanya | Downloads and verifies the dataset, creates the shared stratified split and manifest, then combines the four result files into the final comparison. |
| [`01_model_a_standard.ipynb`](notebooks/01_model_a_standard.ipynb) | Rajitha | Trains a higher-capacity standard CNN with Conv2D, batch normalization, max pooling, dropout, and dense layers for 30 epochs. |
| [`02_model_b_lightweight_optimizer.ipynb`](notebooks/02_model_b_lightweight_optimizer.ipynb) | Dhilanka | Builds a depthwise-separable CNN with fewer than 100,000 trainable parameters and compares Adam, SGD, and SGD with momentum over 20 epochs each. The optimizer is selected using validation performance only. |
| [`03_mobilenetv2.ipynb`](notebooks/03_mobilenetv2.ipynb) | Rajitha | Trains an ImageNet-pretrained MobileNetV2 classifier head for 5 epochs, then fine-tunes the final 20 backbone layers for 15 epochs. |
| [`04_efficientnetb0.ipynb`](notebooks/04_efficientnetb0.ipynb) | Thiwanka | Trains an ImageNet-pretrained EfficientNetB0 classifier head for 5 epochs, then fine-tunes the final 20 backbone layers for 10 epochs. |

## Experiment outputs

Each model is evaluated on the same held-out test split and reports:

- Accuracy, macro precision, and macro recall
- Confusion matrix and classification report
- Total/trainable parameter count
- Saved model size
- Average epoch time and inference latency
- Approximate MACs where implemented

The model notebooks export `model_a.json`, `model_b.json`, `mobilenetv2.json`, and `efficientnetb0.json` to `EN3150_A03_SHARED/shared_results_jute_pest/` in Google Drive. Notebook 00 reads those files and produces `final_model_comparison.csv` plus accuracy-versus-size and accuracy-versus-parameter plots.

## Running in Google Colab

1. Run notebook 00 first to download the UCI archive and create `jute_pest_split_manifest.csv` and `dataset_summary.json`.
2. Make the `EN3150_A03_SHARED` Drive folder available to every group member.
3. Run notebooks 01–04 using the same shared manifest.
4. After all four JSON result files exist, rerun the final-comparison section of notebook 00.

Personal Drive directories hold dataset caches, checkpoints, training logs, and plots. The shared directory holds only the split metadata and compact cross-model results. Keras checkpoints and `BackupAndRestore` support recovery after a Colab runtime disconnect.

Do not commit the downloaded dataset archive, extracted images, checkpoints, or trained model files to Git.
