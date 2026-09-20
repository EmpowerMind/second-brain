# Article: Introduction — Jev (TypeSafe AI)

| | |
|---|---|
| **Source** | [docs.typesafe.ai/introduction](https://docs.typesafe.ai/introduction) |
| **Markdown source** | [docs.typesafe.ai/introduction.md](https://docs.typesafe.ai/introduction.md) |
| **Docs index** | [docs.typesafe.ai/llms.txt](https://docs.typesafe.ai/llms.txt) |
| **Topic** | Jev, System One models, typed AI primitives |
| **Saved** | Sep 20, 2026 |
| **Local copy** | [introduction.md](./introduction.md) — markdown copied from the page |
| **Also here** | [ai-primer.md](./ai-primer.md) — markdown copy of [AI primer](https://docs.typesafe.ai/introduction/machine-learning-primer) |

## TL;DR

Jev is TypeSafe's flagship "System One" model: instead of generating text, it evaluates typed questions against a state and returns structured answers (values, probability distributions, confidence) that code can branch on directly.

## Key points

- **The mismatch it targets** — LLMs generate text for humans; using them for machine-consumed judgments means coercing structured decisions out of prose and parsing them back.
- **Three primitives** — `Choice` (pick from a list → choice, probabilities, confidence), `Score` (rate against a rubric → score, probabilities, confidence), `Noul` (is this statement true → 0–1).
- **Parallel, isolated evaluation** — all question types can be mixed in one API call; each is evaluated independently against the same state, so more questions barely add latency and don't cause context-rot.
- **Atomic questions, composed in code** — decompose anything needing extended reasoning or multi-factor weighing into separate questions, then combine results with your own formula; re-weighting becomes a coefficient change, not a prompt rewrite.
- **Confidence as architecture** — Choice and Score return confidence, usable to decide whether and how to act on an answer.

## AI primer (companion page)

- **Machine Native Intelligence** — TypeSafe bets automation will be ~99% machine-to-machine, so the machine interface matters more than the chat interface; the target is AI with software-like properties (structure, reliability, observability, testability, speed, consistency, low cost).
- **Three post-training paths** — RLHF (chatbots, trained on human preference), RLVR (reasoning models, verifiable rewards, slower/costlier), and TypeSafe's RLCD: reinforcement learning for calibrated decisions.
- **Calibration** — outputs assigned probability 0.2 should be right ~20% of the time, 0.8 ~80%; that holds across groups of predictions, not any single answer.
- **RLHF's failure modes** — rewards sycophancy and confident-sounding hallucination, and causes mode dropping (a milder mode collapse) that narrows the output distribution.
