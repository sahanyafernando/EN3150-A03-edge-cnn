# Colab Runtime Disconnect Recovery

## Why this project is resilient

The notebook stores persistent state on Google Drive rather than only in `/content`.

Each experiment has:
- Keras BackupAndRestore state
- best validation checkpoint
- completed final model
- epoch metric log
- epoch timing log

## Recovery steps

After a runtime disconnect:

1. Reconnect to a Colab runtime.
2. Select GPU again if necessary.
3. Run the import/setup cells.
4. Mount Drive.
5. Recreate the dataset pipelines.
6. Re-run model/function-definition cells.
7. Re-run the experiment cell that was interrupted.

If the experiment is unfinished, Keras should restore the latest backup.
If it is finished, `final.keras` is loaded and the run is skipped.

## Where files are stored

Default Drive folder:

`MyDrive/EN3150_A03/`

Important subfolders:

- `tfds_data/`
- `artifacts/`
- `results/`

## To intentionally restart one experiment

In the notebook:

```python
reset_run("model_b_adam")
```

Then rerun that training cell.

## Practical tips

- Keep your notebook itself in Drive or GitHub.
- Make a Git commit after each real stage.
- Avoid keeping other GPU-heavy tabs/jobs open.
- Do not rely on `/content` for anything you cannot afford to lose.
- Avoid JavaScript "keep alive" hacks; they do not replace checkpointing and may violate service expectations.
