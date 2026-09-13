# EN3150 Assignment 03 — Report Checklist

Use this only as a checklist. Write the discussion from your own experimental outputs.

## 1. Data Preparation
- [ ] Dataset name and source
- [ ] Why it is suitable for low-resolution classification
- [ ] Original image characteristics
- [ ] Final resolution = 64×64 or lower
- [ ] Training = 70%
- [ ] Validation = 15%
- [ ] Test = 15%
- [ ] Number of classes and class names

## 2. Custom Architecture Design
### Model A
- [ ] Architecture diagram/table
- [ ] Conv kernel sizes
- [ ] filter counts
- [ ] pooling details
- [ ] dense units
- [ ] total trainable parameter calculation

### Model B
- [ ] Separable-convolution architecture
- [ ] kernel sizes
- [ ] filter counts
- [ ] dense units
- [ ] total trainable parameter calculation
- [ ] demonstrate total < 100,000
- [ ] explain depthwise + pointwise convolution

### Activation justification
- [ ] Explain why ReLU is hardware-friendly
- [ ] Note that hidden ReLU avoids expensive exponential functions
- [ ] Explain use of logits / prediction with argmax

## 3. Optimizer Selection & Tuning
- [ ] State chosen optimizer
- [ ] State learning rate
- [ ] Explain why chosen
- [ ] Compare Adam vs standard SGD
- [ ] Compare Adam vs SGD + Momentum
- [ ] Explain momentum parameter and convergence effect
- [ ] Include measured curves/table

## 4. Custom Model Training & Evaluation
- [ ] Model A trained >=20 epochs
- [ ] Model B trained >=20 epochs
- [ ] Training loss curve
- [ ] Validation loss curve
- [ ] Test accuracy
- [ ] Confusion matrix
- [ ] Precision
- [ ] Recall
- [ ] Model A/B comparison table:
  - [ ] parameter count
  - [ ] estimated/saved model size
  - [ ] training time per epoch
  - [ ] test accuracy
- [ ] Discuss standard vs separable convolution trade-offs

## 5. Lightweight SOTA Fine-Tuning
- [ ] MobileNetV2
- [ ] EfficientNetB0
- [ ] Same train/validation/test split
- [ ] Fine-tuning method stated
- [ ] Test metrics
- [ ] Total parameter count
- [ ] Model size in MB

## 6. Final Comparison
- [ ] Model B vs MobileNetV2 vs EfficientNetB0
- [ ] Accuracy
- [ ] Memory footprint
- [ ] Computational-cost proxy / measured latency
- [ ] Advantages of sub-100k custom model
- [ ] Limitations of sub-100k custom model
- [ ] Advantages of pretrained lightweight model
- [ ] Limitations of pretrained lightweight model
- [ ] Deployment recommendation for constrained hardware

## GitHub
- [ ] Repository/profile link included in report
- [ ] Multiple real commits made during development
- [ ] No credentials committed
- [ ] No large checkpoints/datasets committed

## Submission
- [ ] Report and code submitted separately
- [ ] Required filename format followed
- [ ] Names and index numbers included
- [ ] Code is commented and runnable
- [ ] Final interpretation is written in your own words
