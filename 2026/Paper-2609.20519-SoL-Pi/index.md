# Paper: SoL-Pi: Recursively Scaling Auto-Research Loops for Efficient Agent Harness

| | |
|---|---|
| **arXiv** | [2609.20519](https://arxiv.org/abs/2609.20519) |
| **PDF** | [https://arxiv.org/pdf/2609.20519](https://arxiv.org/pdf/2609.20519) |
| **HTML (full text)** | [arxiv.org/html/2609.20519v1](https://arxiv.org/html/2609.20519v1) |
| **Code** | [github.com/NVlabs/SoL-Pi](https://github.com/NVlabs/SoL-Pi) |
| **Blog post** | [nvlabs.github.io/SoL-Pi](https://nvlabs.github.io/SoL-Pi/) — notes in [blog.md](./blog.md) |
| **Published** | September 2026 (v1) |
| **Authors** | Haozhe Liu, Tian Ye, Sensen Gao, Qihang Cao, Yitong Li, Mingchen Zhuge, Duomin Wang, Ruihua Zhang, Ping Luo, Jiawang Bian, Lei Zhu, Ligeng Zhu, Enze Xie, Song Han |
| **Affiliation** | NVIDIA, NTU, MIT |
| **Subject** | cs.AI / cs.SE |
| **Local copy** | [paper.md](./paper.md) — full text converted to Markdown |
| **Project page notes** | [blog.md](./blog.md) — the 152-idea pool, orchestration history, per-mechanism search traces |

## TL;DR

An AI-run research loop searches the *agent harness* (not the model) for token-efficiency wins. Four surviving mechanisms cut recorded token traffic ~45–49% and API cost by about a third at comparable task scores, and transfer to an unseen model backend without re-tuning.

## Abstract

As coding agents move from supervised code completion to unattended, around-the-clock exploration, their work expands from isolated predictions into long trajectories of reasoning, tool use, and feedback. Token efficiency therefore becomes important for scaling recursive self-improvement. We take an RSI-inspired approach at the harness layer, scaling auto-research loops across increasingly numerous and diverse environments for harness rollouts. At this scale, the process yields reusable improvements that transfer beyond their development setting, moving automated harness discovery toward production-level outcomes. Four mechanisms survive selection and form SoL-Pi, spanning action execution, context compaction, observation handling, and delegated reading. On the 51-task EdgeBench evaluation, SoL-Pi achieves performance comparable to Pi across GPT-5.6 Sol and Opus 5 while reducing recorded token traffic by 44.7–49.0% and API cost by about one third. In other words, estimated hourly savings are $8.75–$13.50 relative to native Codex and Claude Code harnesses, and $4.36–$5.71 relative to Pi.

## Key points

- **Optimize the harness, not the model** — orthogonal to cheaper tokens (kernels, serving, quantization, smaller models). No training required; the base harness is Pi and only the wrapper changes.
- **Broad-to-deep auto-research funnel** — 152 proposed directions across six families (context, progress, tools, delegation, prompt/policy, improvement & evaluation); ~500 executable environments; >3,000 runs; >60,000 agent–environment interactions. Each lineage is a disposable instance of a shared skill template running a Ralph-Loop-style implement → review → evaluate cycle.
- **Hard isolation between search and validation** — capability metrics, tolerances and efficiency metrics are frozen up front and kept outside the optimizing agent's control. Two gates: capability must stay inside its tolerance, *and* at least one efficiency metric must improve. EdgeBench is held out; failed held-out validation rejects a candidate rather than triggering more optimization.
- **Search environments** — 535 total: 495 GitHub issue→PR repository tasks (PR and regression test hidden; test must fail pre-patch and pass post-patch) + 40 verifier-driven synthetic tasks in a Terminal-Bench-2-style interface.

### The four retained mechanisms

| Mechanism | Acts on | What it does |
|---|---|---|
| **Action Fusion** | action execution | Folds a file mutation and its follow-up command (test/build/run) into one tool request, cutting 3 API calls to 2. Commands needing to inspect the mutation stay separate. |
| **Online Context Compact** | context management | At each `update_plan` step-completion boundary, projects remaining model requests and compares input savings against prompt-cache rewrite cost; compacts only when the gate passes (or near the context limit). Later compactions need a larger margin. |
| **ObservationPack** | observation storage | Archives tool outputs >10 KiB locally, sends them in full for two provider requests, then substitutes a stable handle + size + head/tail excerpt (~1 KB). Exact pages retrievable on demand. |
| **Evidence-Preserving Reducer** | delegated reading | Build/test logs ≥4 KiB go to a cheap model (GPT-5.6 Luna) that extracts a compact "receipt"; a deterministic verifier checks schema, source hash, exit status, exact quotes and size, with fallback to the original log. File reads and searches bypass it. |

Ordering matters: the Reducer runs before ObservationPack, which recognizes the receipt marker and skips those results.

### Results

- **EdgeBench (51 public tasks)** — *Efficiency* point (all four): 1.10 B tokens, −49.0% vs Pi, keeps 93.7% of Pi's score (42.0 vs 44.8), token cost −33.2%. *Performance* point (best single mechanism): score 44.8 → 47.2 (+5.3%) with −6.1% tokens.
- **Transfer to Opus 5** — applied unchanged (developed on GPT-5.6 Sol): keeps 94.3% of Pi's score, −44.7% token traffic, −33.5% API cost. Best single mechanism on Opus 5 is Action Fusion (score 50.48 vs Pi's 44.76).
- **Terminal-Bench 4 (63 CPU tasks)** — solves 15 vs 18 for Codex/Pi, but total cost $211 vs $286 and cost-per-solved $14.07 vs $15.91.
- **IMO 2026 (Lean 4 verified)** — 3/6 passed at $62.69 total, lowest cost per passed problem ($20.90 vs $22.89 Codex, $25.32 Pi). Codex still passes the most (5/6).
- **Agent swarm (kernel optimization, 2h)** — 20 SoL-Pi workers reach 1,127 cycles at $60.11 vs 1,366 cycles at $82.12 for the Pi-baseline swarm (−26.8% cost); a single agent is cheapest at $39.20 but only reaches 1,333 cycles.

### Things worth remembering

- **Cache reuse is not the objective.** Shortening context breaks cached prefixes, so cache-write traffic rises (0.0141 B → 0.0316 B) while cache-read falls (2.13 B → 1.06 B); total cost still drops $1,339 → $894. Judge full task cost, not cache hit rate.
- **Efficiency and capability trade off, and they're separate operating points.** The full stack is the cheap point; a *single* mechanism is the strong point. Stacking everything costs ~2.8 score points on EdgeBench.
- **Mechanisms are backend-sensitive.** Trigger rate and intensity are both lower on Opus 5 (the harness was searched on GPT-5.6 Sol trajectories only) — yet efficiency still improves wherever they fire.
- **Honest scoping by the authors** — the run counts "do not establish a scaling law"; complementarity between mechanisms is "descriptive" since each is measured on its own triggered-task subset; *recursive efficient improvement* is stated as a vision, not a demonstrated result.

## Only on the project page

The [blog notes](./blog.md) cover what the paper leaves out:

- The complete **152-idea proposal pool** by family (Context 24 · Progress 26 · Tools 26 · Delegation 15 · Prompt & policy 15 · Improvement & evaluation 46), including the ideas recorded as *negative* results.
- **Three orchestration designs** they went through — compiled YAML workflow → agent-written code orchestration (a new experiment could take >10 hours of coordinator changes) → disposable skill loop.
- **Per-mechanism search traces**: Action Fusion's 12.3% oracle estimate and non-monotonic 28.3→100% trigger curve over ten batches; ObservationPack frozen at 315 lines / two hooks, one of eight swept configs inside the quality gate, and a paired A/B where response count moved only 0.20%.
- **~1 in 40 starting ideas survived validation**, and after 5–10 iterations even GPT-5.6 Sol at xhigh settled into a local basin — which is the argument for breadth over depth.
- **Why EdgeBench**: the only public benchmark they found supporting 2–12 hours of continuous work, and that horizon is what makes per-turn waste measurable at all.

## Why I saved this

Practical, implementable harness patterns that apply to any long-running coding-agent setup — the big-observation handle, the cache-aware compaction gate, and the verified log-reduction receipt are all reusable ideas independent of Pi.

## Related work referenced

- Meta-Harness ([2603.28052](https://arxiv.org/abs/2603.28052)) — end-to-end optimization of model harnesses
- Recursive Harness Self-Improvement ([2607.15524](https://arxiv.org/abs/2607.15524))
- AHE: Agentic harness engineering ([2604.25850](https://arxiv.org/abs/2604.25850))
- AutoHarness ([2603.03329](https://arxiv.org/abs/2603.03329)) · MemoHarness ([2607.14159](https://arxiv.org/abs/2607.14159))
- Rethinking the evaluation of harness evolution ([2607.12227](https://arxiv.org/abs/2607.12227)) — the overfitting critique this paper responds to
- ACON ([2510.00615](https://arxiv.org/abs/2510.00615)) · Context-Folding ([2510.11967](https://arxiv.org/abs/2510.11967)) · AgentFold ([2510.24699](https://arxiv.org/abs/2510.24699))
- Darwin Gödel Machine (ICLR 2026) · Hyperagents ([2603.19461](https://arxiv.org/abs/2603.19461))

---

*Added to second-brain on 2026-09-21.*
