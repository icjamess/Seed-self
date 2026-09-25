# 00 — CHOOSING THE CLOUD ENVIRONMENT (phone-only operator)

You need a GPU you do not own, reachable from a phone browser, that can be
driven from a notebook page. Four viable options, ranked for your constraints.

| Platform | Free tier | Phone browser | Session limit | Best for |
| --- | --- | --- | --- | --- |
| **Google Colab** | yes, T4 16 GB | workable | ~12 h, idle disconnects | **start here** |
| **Kaggle Notebooks** | yes, ~30 h/week GPU | workable | 12 h | longer runs, free |
| **Lightning AI** | monthly free credits | good | persistent studio | when you outgrow free |
| **RunPod / Vast.ai** | paid, ~$0.30–0.80/h | adequate | as long as you pay | big runs, 24 GB+ cards |

**Recommendation:** Colab free tier for the first fine-tune, Kaggle when you
need the weekly hours, rented A100 hours only once the recipe is proven. Do not
pay for compute until a free run has produced a model you have actually tested.

**Not viable for training:** Render, Vercel, and similar app hosts. They serve
web services, not GPU jobs. Render is still useful later for *hosting* a trained
model behind an API; it is not where training happens.

## Phone browser reality

- Colab and Kaggle both work in mobile Chrome or Safari. Cells run, output
  shows, files download.
- Typing code on a phone is miserable. This kit avoids it: the notebook is
  pre-written, and you edit **one configuration cell** and press run.
- Keep the tab in the foreground. Mobile browsers suspend background tabs and
  the session drops.
- A cheap Bluetooth keyboard changes this experience entirely, if you ever want one.

## Accounts to create first

1. **Google account** — for Colab and Drive.
2. **Hugging Face account** — free. This is where models are downloaded from and
   where your finished model gets stored. Create a token under Settings, Access
   Tokens, with write permission.
3. **Kaggle account** — optional, for the weekly GPU hours.

Nothing else is required.
