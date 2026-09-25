# 01 — THE PIPELINE, END TO END

What actually happens, in order, and where each step runs.

```
  [1] curate dataset        phone or laptop, plain text   -> data/*.jsonl
  [2] upload to Drive/HF    phone                          -> cloud storage
  [3] fine-tune             Colab GPU, 20-60 min           -> LoRA adapter
  [4] evaluate held-out     same notebook                  -> pass/fail numbers
  [5] merge + quantize      same notebook                  -> model.gguf
  [6] download / push       to phone or Hugging Face       -> your model
  [7] run locally           PocketPal on your phone        -> offline, yours
```

## What each step is

**[1] Curate.** The part that carries your hypothesis. You are not collecting
volume, you are selecting coverage. See `guides/02-DATASET-DESIGN.md`.

**[2] Upload.** Mount Google Drive in the notebook, or push the dataset to a
private Hugging Face dataset repo. Drive is simpler from a phone.

**[3] Fine-tune.** You are NOT training from scratch. You take an existing
open-weight small model (Qwen3 1.7B, Llama 3.2 3B) and adjust it on your data
using **LoRA** — a method that trains a small set of extra weights rather than
all of them. This is why a free T4 suffices and why the run takes minutes.

**[4] Evaluate.** Held-out set, scored before and after. Your Wordcraft
discipline transfers directly here: the test items must not appear in training,
and you report the number, not the impression.

**[5] Merge and quantize.** Fold the LoRA adapter into the base model, then
compress to 4-bit GGUF so it runs on a phone.

**[6] Download.** The GGUF file is 1–2 GB. Push it to your Hugging Face account,
then download to the phone over WiFi.

**[7] Run.** Load the GGUF as a custom model in PocketPal. Airplane mode. Yours.

## Total cost

Zero, on free tiers, for the first several iterations.

## Total wall-clock, realistic

First attempt: an afternoon, most of it learning the interface.
Subsequent iterations: 30–60 minutes each.
