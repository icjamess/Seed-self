# 02 — DATASET DESIGN (where your hypothesis lives)

This is the step that matters. Everything else is machinery.

## Format

JSONL — one JSON object per line, each with a user message and the response you
want. Example:

```json
{"messages":[{"role":"user","content":"What is the Law of Non-Solicitation."},{"role":"assistant","content":"A standing constraint: answers end decisively, without questions or permission-asks."}]}
```

Files in `data/`:
- `train.jsonl` — what the model learns from
- `eval.jsonl` — held out, never trained on, used to score

## The selection principles, carried over from Wordcraft

**1. Coverage of the relation, not volume of examples.** The finding that
mattered: repetition is harmless, missing coverage is fatal. Enumerate the
*kinds* of thing you want it to do, then make sure every kind is present.
Adding a fifth example of a kind already covered buys less than adding the
first example of a kind that is missing.

**2. Select along the dimension you will test.** Balanced selection won by
spending its budget on the exact contrast the evaluation scored. Decide what
"working" means before choosing examples, then choose for that.

**3. Diversity along the task axis specifically.** Different task types beat
different surface wordings of the same task.

**4. Quality over quantity, strongly, at this size.** Small models are more
sensitive to low-quality data than large ones. One sloppy example costs more
here than it would in a large corpus.

## Realistic sizes

| Goal | Examples needed |
| --- | --- |
| Style and format adherence | 100–500 |
| A narrow domain skill | 500–2,000 |
| Broad domain competence | 5,000–50,000 |

Start at 200. A 200-example run takes minutes and tells you whether the pipeline
works. Scale after the loop closes, not before.

## Where examples come from

- **Your own archive.** Your existing writing, capsules, notes, and transcripts are a curated corpus that exists already. This is the highest-quality source you have and nobody else has it.
- **Generated then filtered.** Have a large model produce candidates, then you keep or cut each one. This is distillation in its practical form, and it is how the Phi line was built.
- **Never unfiltered web text.** At this scale it poisons more than it teaches.

## The discipline that makes it research rather than tinkering

Hold out an evaluation set before you start. Do not look at it while tuning.
Report the score you got, not the score you hoped for. Log the dataset version,
the seed, and the settings with every run.
