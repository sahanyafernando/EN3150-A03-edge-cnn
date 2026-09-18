# EN3150 Assignment 03 — Team Task Assignment

## Team

- **Sahanya** 
- **Rajitha**
- **Dhilanka**
- **Thiwanka**

The assignment requires shared data preparation, two custom CNNs, optimizer comparison, evaluation, two lightweight pretrained/SOTA networks, and a final accuracy-memory-computational-cost comparison.

## Notebook ownership

```text
00_data_check.ipynb          -> Sahanya
01_model_a_standard.ipynb    -> Rajitha
02_model_b_lightweight.ipynb -> Dhilanka
03_mobilenetv2.ipynb         -> Rajitha
04_efficientnetb0.ipynb      -> Thiwanka
05_final_comparison.ipynb    -> Sahanya
```

# Sahanya — shared data, GitHub, integration, final comparison

## Coding

Own:

```text
00_data_check.ipynb
05_final_comparison.ipynb
```

Prepare and verify common configuration:

```text
Dataset: TF Flowers
Image size: 64 x 64
Train: 70%
Validation: 15%
Test: 15%
Seed: 42
```

`00_data_check.ipynb` should show:

- classes
- sample counts
- exact split sizes
- example resized images
- preprocessing settings

`05_final_comparison.ipynb` should collect:

```text
Model
Parameters
Model size
Test accuracy
Precision
Recall
Training/inference cost where measured
```

## GitHub

- create/manage repository
- add collaborators
- maintain `main`
- review Pull Requests
- merge approved work
- resolve conflicts
- protect repository from large models/datasets/secrets

## Report

Integrate/write:

- introduction
- data preparation
- final comparison
- accuracy vs memory vs computational-cost discussion
- deployment recommendation
- conclusion
- final formatting and submission checks

# Rajitha — Model A + MobileNetV2

Branch:

```text
feature/rajitha-model-a-mobilenet
```

## Model A

Notebook:

```text
01_model_a_standard.ipynb
```

Tasks:

- standard Conv2D + MaxPooling CNN
- list kernel sizes, filters, dense units
- calculate trainable parameters
- explain ReLU choice
- train >=20 epochs
- plot training/validation loss
- calculate test accuracy
- calculate precision and recall
- confusion matrix
- model size
- average training time/epoch

## MobileNetV2

Notebook:

```text
03_mobilenetv2.ipynb
```

Tasks:

- ImageNet pretrained MobileNetV2
- exact same dataset split
- classifier-head training
- fine-tune part of backbone
- evaluate accuracy, precision, recall, confusion matrix
- record total/trainable parameters
- record model size in MB

## Report

Draft:

- Model A architecture/results
- MobileNetV2 method/results

## Suggested commits

```text
feat: implement standard CNN model A
exp: train model A for 20 epochs
analysis: add model A metrics and confusion matrix
feat: add MobileNetV2 transfer learning
analysis: add MobileNetV2 evaluation results
```

# Dhilanka — Model B + optimizer comparison

Branch:

```text
feature/dhilanka-model-b-optimizer
```

Notebook:

```text
02_model_b_lightweight.ipynb
```

## Model B

Tasks:

- use depthwise-separable convolution (`SeparableConv2D` or equivalent)
- keep trainable parameters below 100,000
- list kernel sizes, filters, dense units
- calculate parameter count
- calculate/estimate MAC reduction where possible
- explain why separable convolution reduces compute/parameters
- explain hardware-friendly activation choice

## Optimizer comparison

Use the same Model B architecture and same data split.

Compare:

```text
Adam
SGD
SGD + Momentum
```

Suggested starting settings:

```text
Adam: lr = 0.001
SGD: lr = 0.01
SGD + Momentum: lr = 0.01, momentum = 0.9
```

Generate:

- validation loss comparison
- validation accuracy comparison
- convergence discussion
- explanation of momentum

Then train the chosen Model B configuration for >=20 epochs and evaluate:

- test accuracy
- precision
- recall
- confusion matrix
- model size
- average time/epoch

## Report

Draft:

- Model B architecture
- standard vs separable convolution
- parameter/MAC explanation
- optimizer comparison
- momentum explanation
- Model B results
- Model A vs Model B trade-off notes

## Suggested commits

```text
feat: implement sub-100k lightweight CNN
analysis: add parameter and MAC calculations
exp: compare Adam SGD and momentum
exp: complete 20 epoch model B training
analysis: add model B test metrics
```

# Thiwanka — EfficientNetB0 + SOTA comparison support

Branch:

```text
feature/thiwanka-efficientnet-evaluation
```

Notebook:

```text
04_efficientnetb0.ipynb
```

Tasks:

- ImageNet pretrained EfficientNetB0
- same 70/15/15 split
- same 64 x 64 input
- classifier-head training
- fine-tune suitable final layers
- training curves
- test accuracy
- precision
- recall
- confusion matrix
- total/trainable parameters
- model size in MB
- training time

After Rajitha sends MobileNetV2 results, prepare a small:

```text
MobileNetV2 vs EfficientNetB0
```

comparison with accuracy, parameters, model size, and training/inference observations.

## Report

Draft:

- EfficientNetB0 method/results
- MobileNetV2 vs EfficientNetB0 comparison notes
- limitations/advantages of pretrained edge models

## Suggested commits

```text
feat: add EfficientNetB0 transfer learning
exp: fine tune EfficientNetB0
analysis: add EfficientNetB0 metrics
analysis: compare pretrained model results
```

# Shared rules

- Same dataset for everybody.
- Same 70/15/15 split.
- Same 64 x 64 resolution.
- Never use test data for training or optimizer tuning.
- Save long-run checkpoints to Google Drive.
- Record results immediately after training.
- Each member writes a brief interpretation of their own results.

# Definition of Done

For each assigned model:

- [ ] architecture complete
- [ ] notebook runs
- [ ] parameter count recorded
- [ ] required training completed
- [ ] loss curves generated
- [ ] test accuracy recorded
- [ ] precision recorded
- [ ] recall recorded
- [ ] confusion matrix generated
- [ ] model size recorded
- [ ] timing recorded where required
- [ ] brief interpretation written
- [ ] commits pushed
- [ ] Pull Request created
- [ ] Sahanya reviewed PR

# Final result summary to Sahanya

Each member sends:

```text
Member:
Model:
Parameter count:
Model size:
Best validation accuracy:
Test accuracy:
Precision:
Recall:
Average epoch time:
Inference timing if measured:
Important observation:
PR link:
```

The workload is intentionally distributed by experiment rather than simply one model per person:

- Sahanya: GitHub + shared data + integration + final report
- Rajitha: simpler custom Model A + MobileNetV2
- Dhilanka: key lightweight Model B + optimizer experiments
- Thiwanka: EfficientNetB0 + SOTA comparison support
