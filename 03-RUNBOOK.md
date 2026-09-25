# 03 — RUNBOOK: first fine-tune from a phone

Follow in order. Nothing here requires typing code.

## Before you begin
- Google account, Hugging Face account (free, token with write permission).
- The notebook `notebooks/seed_self_finetune.ipynb` in your Google Drive, or committed to the repo and opened from there.

## Run
1. **Open the notebook.** From Drive: tap the file → Open with → Google Colaboratory. From GitHub: colab.research.google.com → GitHub tab → paste the repo URL.
2. **Set the GPU.** Runtime → Change runtime type → T4 GPU → Save. Skipping this is the most common failure.
3. **First run, as-is.** Runtime → Run all. `use_sample` is True, so it runs on four bundled examples and proves the pipeline end to end. Expect 10–20 minutes, mostly installing.
4. **Read cells 5 and 7.** Same held-out questions, before and after. That comparison is the entire result.
5. **Then use your own data.** Put `train.jsonl` and `eval.jsonl` in Drive under `seed-self/`, set `use_sample` to False, rerun.
6. **Export.** Cell 8 makes the GGUF. Cell 9 pushes it to Hugging Face or offers a download.
7. **Load on the phone.** Download the GGUF, add it in PocketPal as a local model, airplane mode, test.

## Keeping the session alive from a phone
- Keep the Colab tab in the foreground. Backgrounded mobile tabs get suspended and the runtime disconnects.
- Free sessions cap around 12 hours and disconnect when idle. A 200-example run finishes in minutes, so this rarely bites.
- If it disconnects mid-run, rerun from cell 2. Nothing is lost but time.

## What to log each run
Dataset version, number of examples, seed, learning rate, epochs, and the
held-out result. Without that record, run six is unattributable to any cause.

## Cost control
Free tier throughout. Do not rent GPU hours until a free run has produced a
model you have loaded on your phone and actually used.
