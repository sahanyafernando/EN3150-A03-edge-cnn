# EN3150 Assignment 03 — Resource-Constrained CNN

This repository accompanies a Colab notebook for EN3150 Assignment 03.

## Contibutors
1. FERNANDO G.S.S. 230179K - fernandogss.23@uom.lk - Computer Science & Engineering
2. HEWAWASAM H.R.L. 230223R - HEWAWASAM H.R.L. 230223R - Electrical Engineering
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

## Dataset

For this assignment, we selected the **TensorFlow Flowers (`tf_flowers`) dataset**.

Dataset link:

https://www.tensorflow.org/datasets/catalog/tf_flowers

The dataset contains **3,670 RGB flower images** belonging to **5 different classes**:

- Daisy
- Dandelion
- Roses
- Sunflowers
- Tulips

The dataset is available directly through **TensorFlow Datasets (TFDS)**, which makes it easy to load and use in Google Colab without manually uploading a large dataset. :contentReference[oaicite:0]{index=0}

### Why we selected this dataset

We selected the `tf_flowers` dataset because it is suitable for the requirements of this assignment.

The main reasons are:

- It is an **image classification dataset** with multiple classes.
- It is not CIFAR-10, which is not allowed for this assignment.
- The dataset is not very large, so it is practical to train several models within the available Colab resources and time.
- The images can be resized to **64×64 pixels**, which allows us to simulate an edge or resource-constrained image classification environment.
- It has enough images and visual variation to properly compare the performance of a standard CNN, a lightweight CNN, and pre-trained models.
- It is directly supported by TensorFlow Datasets, therefore the same dataset and data split can easily be reproduced by all group members.
- Since our assignment mainly focuses on the trade-off between **accuracy, memory footprint, and computational cost**, this dataset gives us a simple and manageable problem where we can focus more on comparing the models rather than spending too much time on dataset preparation.

For all experiments, the images are resized to:

```text
64 × 64 × 3
