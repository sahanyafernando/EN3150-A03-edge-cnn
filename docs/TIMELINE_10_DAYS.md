# EN3150 Assignment 03 — 10-Day Team Timeline

Goal: finish the main experiments by Day 7–8 so Day 10 is only a buffer/final-check day.

## Day 1 — Setup

### Sahanya
- Create/clean repository.
- Invite Rajitha, Dhilanka, Thiwanka.
- Add notebook structure.
- Share team guide and assignments.

### Rajitha / Dhilanka / Thiwanka
- Accept invitation.
- Install/sign in to GitHub Desktop.
- Clone repository.
- Create assigned branch.
- Push one setup commit to confirm workflow.

### Checkpoint
Everyone can clone, branch, commit, and push.

## Day 2 — Data + architectures

### Sahanya
Complete shared dataset check and exact split settings.

### Rajitha
Implement Model A architecture.

### Dhilanka
Implement Model B and verify parameter count <100,000.

### Thiwanka
Create EfficientNetB0 training skeleton.

Each active member should have at least one meaningful commit.

## Day 3 — Sanity training

### Rajitha
Run short tests for Model A and MobileNetV2.

### Dhilanka
Run short Model B test.

### Thiwanka
Run short EfficientNetB0 test.

### Sahanya
Verify all notebooks use identical data settings.

Do not start expensive long runs until the data setup matches.

## Day 4 — Main custom training

### Rajitha
Start/complete 20-epoch Model A training.

### Dhilanka
Start Adam vs SGD vs SGD+Momentum experiments.

### Thiwanka
Begin EfficientNetB0 training/fine-tuning.

### Sahanya
Review code/PR progress and shared settings.

## Day 5 — SOTA + optimizer work

### Rajitha
Train MobileNetV2.

### Dhilanka
Finish optimizer comparison and choose Model B optimizer.

### Thiwanka
Continue/finalize EfficientNetB0.

### Sahanya
Create empty final result/comparison tables and report structure.

## Day 6 — Finish major training

Target: every required model has either a completed run or a resumable Drive checkpoint.

### Rajitha
Finish Model A + MobileNetV2.

### Dhilanka
Finish Model B >=20 epochs.

### Thiwanka
Finish EfficientNetB0.

### All
Push current notebooks and result updates.

## Day 7 — Evaluation

Every model owner calculates:

- test accuracy
- precision
- recall
- confusion matrix
- parameter count
- model size
- training time

Rajitha: Model A + MobileNetV2  
Dhilanka: Model B + optimizer plots  
Thiwanka: EfficientNetB0 + SOTA comparison notes  
Sahanya: collect all numerical results.

## Day 8 — PR + report drafting

### Rajitha / Dhilanka / Thiwanka
- clean notebooks
- add comments
- remove unnecessary debug output
- add interpretation
- push final feature branch
- open PR
- send report section draft

### Sahanya
- review/merge PRs
- build final comparison
- assemble report

## Day 9 — Integration and verification

Check:

```text
same dataset
same split
same image size
correct model names
required metrics
required plots
parameter counts
Model B <100k
two SOTA models
```

### Sahanya
- finish final comparison
- write trade-off discussion
- verify report figures/tables
- check GitHub link and submission checklist

### Other members
Verify the report numbers for the experiments they ran.

## Day 10 — Buffer + submission

Avoid new architecture changes unless absolutely necessary.

Use Day 10 for:

- proofreading
- rerunning only broken/missing cells
- checking filenames
- checking names/index numbers
- checking repository
- checking Moodle files
- final PDF inspection
- submission

Submit several hours before the deadline if possible.

# Recommended commit rhythm

Day 1–2:
```text
setup / architecture
```

Day 3–5:
```text
training / experiment
```

Day 6–7:
```text
evaluation
```

Day 8–9:
```text
analysis / documentation
```

Avoid creating all commits on Day 10.

# Daily 10-minute check-in

Each member answers:

1. What did I finish today?
2. What is currently running?
3. What is blocking me?
4. What will I commit/push today?

If someone is blocked for more than half a day, tell the group immediately rather than waiting until the final days.
