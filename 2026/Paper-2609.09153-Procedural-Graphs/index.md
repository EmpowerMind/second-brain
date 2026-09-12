# Paper: Procedural Graphs: Self-Evolving Execution Structures for LLM Agents

| | |
|---|---|
| **arXiv** | [2609.09153](https://arxiv.org/abs/2609.09153) |
| **PDF** | [https://arxiv.org/pdf/2609.09153](https://arxiv.org/pdf/2609.09153) |
| **HF paper page** | [huggingface.co/papers/2609.09153](https://huggingface.co/papers/2609.09153) |
| **HTML (full text)** | [arxiv.org/html/2609.09153v1](https://arxiv.org/html/2609.09153v1) |
| **Published** | Sep 8, 2026 (submitted to HF Sep 9, 2026 by [taesiri](https://huggingface.co/taesiri)) |
| **Authors** | Yuxing Lu, Yicheng Chen, Shanchan Wu, Sercan Ö. Arık |
| **Affiliation** | Google (also Georgia Institute of Technology, Peking University) |
| **Subject** | cs.AI |
| **Local copy** | [paper.md](./paper.md) — full text converted to Markdown |

## TL;DR

A procedural graph framework organizes agent actions into structured relational triplets, providing situational guidance and self-evolving topology to improve long-horizon tool use.

## Abstract

Large language models are increasingly deployed as agents that plan over long horizons and act through external tools. Most agents select actions through unconstrained generation over an accumulating history, leaving implicit the procedural knowledge of what to do, in what order, and under which conditions. As trajectories lengthen, agents can lose track of their objectives, invoke tools out of order, and repeat unproductive actions. We introduce the Procedural Graph: just as a knowledge graph organizes factual knowledge into (entity, relation, entity) triplets for what-is questions, a Procedural Graph organizes procedural knowledge into (procedure, relation, procedure) triplets for what-to-do questions. At each decision step, the framework localizes the agent's active node, and a guidance model translates the surrounding subgraph into step-level situational guidance that biases the solver's next action without dictating it. The graph is self-evolving: an LLM refiner contrasts failed trajectories with successful ones and edits the graph's topology and attributes, committing edits that preserve or improve held-out validation performance while retaining rejected ones to discourage repetition. Starting from a minimal skeleton, the loop builds graphs that match or surpass hand-designed ones. It can also repair a flawed expert prior. Across multiple datasets, task types, and LLMs, the Procedural Graph delivers consistent gains over memory-based baselines, and self-evolution further improves performance without manual engineering.

## Key points

- **Representation** — a directed, attributed graph $\mathcal{G}=(\mathcal{V},\mathcal{R},\mathcal{E},\Phi)$ of `(procedure, relation, procedure)` triplets. Nodes abstract tool calls, reasoning steps, or task states; edges carry `condition`, `guidance`, and `pitfalls` text. Relation vocabulary: `LEADS_TO`, `TRIGGERS`, `PROVIDES_INPUT_FOR`, `CONVERGES_TO`.
- **Online inference** — *locate* the active node by exact-matching the last action, *extract* its 2-hop neighborhood, *generate* step-level situational guidance with a guidance LLM, then append that guidance to the solver prompt (soft steering, not constrained decoding).
- **Offline self-evolution** — four-step loop: diagnostic rollout → feedback-driven mutation (add/delete nodes and edges) → validation gating (commit only if held-out score does not drop) → rejection memory as negative evidence for later rounds.
- **Results** — first or joint-first in 21 of 24 model×benchmark settings across HotpotQA, MultiChallenge, GDPval, ALFWorld, τ-bench, BFCL v3 (solvers: Claude Sonnet 4.6, Gemini 3.1 Pro, Gemini 3.5 Flash, Grok 4.1 Fast). On EnterpriseArena, survival rises 44%→58% (Sonnet 4.6), 6%→34% (Gemini 3.1 Pro), 26%→40% (Grok 4.1 Fast).
- **Construction modes** — evolving from scratch (Mode 5) beats the hand-crafted expert prior on HotpotQA; the loop also *repairs* a bad expert prior on MultiChallenge (58.93% → 92.86%).
- **Cost** — guidance adds tokens even when it cuts solver steps; localized subgraph guidance is cheaper and better than injecting the full graph.
- **Graphs are small** — 7–17 nodes and 7–27 triplets per benchmark, except BFCL v3 (131 nodes / 265 triplets, mirroring its function catalog).

## Related papers (from the HF page)

- [HiSkill: Empowering LLM Agents with Hierarchical Skill Graphs](https://huggingface.co/papers/2607.25853) (2026)
- [Living-Harness Is an Interactive-Agent Evolver](https://huggingface.co/papers/2607.26598) (2026)
- [HyperSkill: Self-Evolving LLM Agents via Hypergraph-Structured Skill Memory](https://huggingface.co/papers/2608.16114) (2026)
- [CoSkill: Joint Reinforcement Learning of Reasoning and Meta-Skill Agents for Hierarchical Skill Evolution](https://huggingface.co/papers/2609.04865) (2026)
- [Toward Effective and Reliable LLM Agents via Dynamic Ontology](https://huggingface.co/papers/2608.22974) (2026)
- [SkillZip: Contract-Preserving Graph Compression for Scalable Agent Skill Libraries](https://huggingface.co/papers/2608.05604) (2026)
- [SKILL.state: Scalable Long-Horizon Agent Skills](https://huggingface.co/papers/2608.26263) (2026)

---

*Added to second-brain on 2026-09-12.*
