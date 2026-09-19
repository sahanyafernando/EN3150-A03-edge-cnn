# EN3150 Assignment 03 — Team GitHub + Colab Guide

**For Rajitha, Dhilanka, and Thiwanka.**  
Sahanya will manage the repository, review Pull Requests, and merge completed work.

## Golden rule

Each person works on their **own branch** and **own notebook(s)**.

**Do not push directly to `main`.**

## Recommended notebook structure

```text
notebooks/
├── 00_data_check.ipynb
├── 01_model_a_standard.ipynb
├── 02_model_b_lightweight.ipynb
├── 03_mobilenetv2.ipynb
├── 04_efficientnetb0.ipynb
└── 05_final_comparison.ipynb
```

This is recommended because `.ipynb` files are JSON files and are unpleasant to merge when two people edit the same notebook.

### Notebook ownership

```text
Sahanya  -> 00_data_check.ipynb
Rajitha  -> 01_model_a_standard.ipynb
Rajitha  -> 03_mobilenetv2.ipynb
Dhilanka -> 02_model_b_lightweight.ipynb
Thiwanka -> 04_efficientnetb0.ipynb
Sahanya  -> 05_final_comparison.ipynb
```

## Shared experiment settings — do not change independently

Everyone must use the same dataset configuration.

```python
SEED = 42
IMG_SIZE = 64
BATCH_SIZE = 64

splits = [
    "train[:70%]",
    "train[70%:85%]",
    "train[85%:]",
]
```

The final comparison is only fair if all models use the same dataset, same train/validation/test split, same image size, same class mapping, and same test set.

If you want to change a shared setting, discuss it with the group first.

# 1. One-time GitHub setup

## Accept the collaborator invitation

Sahanya will add you to the GitHub repository.

Open the invitation and click **Accept invitation**.

## Install GitHub Desktop

For this assignment, GitHub Desktop is recommended for beginners.

1. Install GitHub Desktop.
2. Sign in using your GitHub account.
3. Choose **File -> Clone repository**.
4. Select the EN3150 repository.
5. Choose a local folder.
6. Click **Clone**.

# 2. Create your branch

Never work directly on `main`.

In GitHub Desktop:

1. Click **Current branch**.
2. Click **New branch**.
3. Create your assigned branch from `main`.
4. Click **Publish branch**.

Use these names:

```text
Rajitha   -> feature/rajitha-model-a-mobilenet
Dhilanka  -> feature/dhilanka-model-b-optimizer
Thiwanka  -> feature/thiwanka-efficientnet-evaluation
```

# 3. Google Colab workflow

Recommended workflow:

```text
GitHub repo
   ↓
local cloned folder
   ↓
upload your assigned notebook to Colab
   ↓
work/train
   ↓
download updated .ipynb
   ↓
replace the same notebook in the local repo
   ↓
commit in GitHub Desktop
   ↓
push
   ↓
open Pull Request
```

## Enable GPU

In Colab:

```text
Runtime
-> Change runtime type
-> GPU
-> Save
```

Check it:

```python
import tensorflow as tf
print(tf.config.list_physical_devices("GPU"))
```

# 4. Save checkpoints to Google Drive

Do not depend only on `/content/` because it is temporary.

```python
from google.colab import drive
drive.mount("/content/drive")
```

Use your own folder:

```text
MyDrive/EN3150_A03/
├── rajitha/
├── dhilanka/
└── thiwanka/
```

This prevents checkpoint/model overwrites.

# 5. Commit your work

After completing a meaningful stage:

1. Download the notebook from Colab:
   `File -> Download -> Download .ipynb`
2. Replace the corresponding notebook inside your cloned project.
3. Open GitHub Desktop.
4. Confirm you are on your own branch.
5. Review the changed files.
6. Enter a meaningful commit message.
7. Click **Commit to your branch**.
8. Click **Push origin**.

Good commit messages:

```text
feat: implement standard CNN architecture
exp: add 20 epoch model A training
analysis: add model A confusion matrix and metrics
feat: add MobileNetV2 transfer learning
exp: fine tune MobileNetV2 backbone
```

Bad commit messages:

```text
update
changes
new
done
final
```

## How often should you commit?

Target **3–6 meaningful commits per person** across the 10 days.

Commit after real stages such as:

```text
architecture finished
training finished
evaluation finished
plots/report notes finished
```

Do not make fake commits just to increase the count.

# 6. Create a Pull Request

When your task is ready for Sahanya to review:

1. Push your branch.
2. Open the repository on GitHub.
3. Click **Compare & pull request**.
4. Set:
   `base: main`
   `compare: your branch`
5. Write what you completed.
6. Click **Create pull request**.
7. Send the PR link to Sahanya.

Example PR description:

```text
Completed Model A:
- standard CNN architecture
- parameter count
- 20 epoch training
- train/validation loss plots
- test accuracy
- precision and recall
- confusion matrix
```

**Do not merge the PR yourself.**  
Sahanya will review and merge.

# 7. Before each work session

Open GitHub Desktop and:

1. Confirm you are on your own branch.
2. Click **Fetch origin**.
3. If Sahanya says shared files changed, sync before continuing.

# 8. Rules that prevent Git problems

1. Do not edit another member's notebook without agreement.
2. Do not push directly to `main`.
3. Do not rename notebooks without telling Sahanya.
4. Do not commit model/checkpoint/data files such as:
   `*.keras`, `*.h5`, `checkpoints/`, `tfds_data/`.
5. Do not commit API keys, GitHub tokens, passwords, or `.env`.
6. Before pushing, make sure the cells you changed run correctly.

# 9. If GitHub Desktop shows a merge conflict

Stop before clicking random conflict-resolution buttons.

Take a screenshot and contact Sahanya.

Because everyone owns separate notebooks, conflicts should be rare.

# 10. Optional terminal commands

If you want to use the terminal instead of GitHub Desktop:

```powershell
git clone REPOSITORY_URL
cd REPOSITORY_NAME

git checkout -b feature/YOUR-BRANCH

git add notebooks/YOUR_NOTEBOOK.ipynb
git commit -m "feat: describe what you completed"

git push -u origin feature/YOUR-BRANCH
```

Later:

```powershell
git add notebooks/YOUR_NOTEBOOK.ipynb
git commit -m "analysis: add test metrics"
git push
```

# 11. What to send the group after each completed experiment

Send:

```text
Model:
Final test accuracy:
Precision:
Recall:
Parameter count:
Saved model size:
Average training time/epoch:
Best validation accuracy:
Important observation:
GitHub PR link:
```

Also keep:

```text
training/validation loss curve
accuracy curve
confusion matrix
parameter table/model summary
```

A model task is complete only when it has working code, results, plots, short interpretation, GitHub commits, and a Pull Request.
