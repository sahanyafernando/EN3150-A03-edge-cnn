# EN3150 Assignment 03 — Resource-Constrained CNN

This repository accompanies a Colab notebook for EN3150 Assignment 03.

## Contibutors
1. FERNANDO G.S.S. 230179K - fernandogss.23@uom.lk - Computer Science & Engineering
2. HEWAWASAM H.R.L. 230223R - hewawasamhrl.23@uom.lk - Electrical Engineering
3. BANDARA W.D.T. 230083K - bandarawdt.23@uom.lk - Electrical Engineering
4. HERATH H.M.D.N.B. 230240P - herathhmdnb.23@uom.lk - Electrical Engineering

## What the notebook covers

- TF Flowers image dataset
- 64×64 RGB preprocessing
- 70% / 15% / 15% train-validation-test split
- Model A: standard Conv2D CNN
- Model B: depthwise-separable CNN below 100,000 parameters
- Adam vs SGD vs SGD+Momentum comparison
- 20-epoch custom-model training
- loss curves
- accuracy, confusion matrix, macro precision and macro recall
- model parameter count, approximate MACs, file size and epoch time
- MobileNetV2 transfer learning
- EfficientNetB0 transfer learning
- final accuracy / memory / latency comparison
- Google Drive checkpoints and automatic recovery after Colab runtime disconnects


### Runtime-disconnect recovery

The notebook uses Google Drive for:

- TFDS cache,
- Keras `BackupAndRestore`,
- best checkpoints,
- final models,
- CSV logs,
- epoch timing.

If Colab disconnects, reconnect and rerun the setup/data/model-definition cells, then rerun the interrupted training cell. It should resume from the persistent backup. If a completed `final.keras` exists, that run is loaded instead of retrained.

This is safer than trying to prevent Colab from disconnecting with browser scripts.


