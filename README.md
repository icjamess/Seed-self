# seed-self — cloud environment

Fine-tune a small open-weight model on your own curated data, from a phone,
on free GPU time, and end with a file that runs offline.

## Order

1. `guides/00-WHICH-CLOUD.md` — pick the platform, create the accounts
2. `guides/01-THE-PIPELINE.md` — what happens at each step and where it runs
3. `guides/02-DATASET-DESIGN.md` — the part that carries the hypothesis
4. `guides/03-RUNBOOK.md` — first run, step by step
5. `notebooks/seed_self_finetune.ipynb` — the notebook itself

## The one-line version

You are not training a model from scratch. You are taking one that exists and
adapting it with a small, deliberately chosen dataset — which is the only
version of "small data, strong performance" that the evidence supports.

## Data

`data/train.example.jsonl` and `data/eval.example.jsonl` show the format.
Replace with your own.

## Open in Colab

Upload the notebook to Drive and open with Colab, or in Colab choose the GitHub
tab and paste this repository's URL.
