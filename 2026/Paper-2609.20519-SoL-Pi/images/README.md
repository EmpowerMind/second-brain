# Figures — provenance

All assets here are the **original source files** published by the authors,
fetched with `curl`. Nothing is a screen capture. Filenames are renamed to be
self-describing; the tables below give the upstream name for each one, and the
scripts reproduce the whole directory from scratch.

## Paper figures (`./`)

Source: the arXiv HTML rendering, <https://arxiv.org/html/2609.20519v1>.

| File | Upstream asset |
|---|---|
| `figure-1-scaling-auto-research-loop.png` | `teaser-funnel-v10.png` |
| `figure-2-broad-to-deep-search.svg` | `parallel-auto-research-loop.svg` |
| `figure-3-search-environments.svg` | `search-environments-heldout.svg` |
| `figure-4-four-mechanisms.png` | `method_v2.png` |
| `figure-5-agent-swarm.svg` | `swarm-overview-side-by-side-v8.svg` |
| `figure-6-backend-activation.svg` | `component_backend_activation.svg` |
| `figure-7-merge-behavior.svg` | `component_configuration_comparison.svg` |
| `figure-8-action-fusion-discovery.svg` | `action-fusion-discovery.svg` |

```bash
cd "$(dirname "$0")"   # this images/ directory
BASE=https://arxiv.org/html/2609.20519v1

curl -fsSL -o figure-1-scaling-auto-research-loop.png "$BASE/teaser-funnel-v10.png"
curl -fsSL -o figure-2-broad-to-deep-search.svg       "$BASE/parallel-auto-research-loop.svg"
curl -fsSL -o figure-3-search-environments.svg        "$BASE/search-environments-heldout.svg"
curl -fsSL -o figure-4-four-mechanisms.png            "$BASE/method_v2.png"
curl -fsSL -o figure-5-agent-swarm.svg                "$BASE/swarm-overview-side-by-side-v8.svg"
curl -fsSL -o figure-6-backend-activation.svg         "$BASE/component_backend_activation.svg"
curl -fsSL -o figure-7-merge-behavior.svg             "$BASE/component_configuration_comparison.svg"
curl -fsSL -o figure-8-action-fusion-discovery.svg    "$BASE/action-fusion-discovery.svg"
```

Six of the eight are vector SVGs upstream and are stored as such, so they stay
sharp at any zoom. Figures 1 and 4 are raster-only upstream.

## Blog figures (`./blog/`)

Source: the project page, <https://nvlabs.github.io/SoL-Pi/>. These keep their
upstream filenames, so the mapping is one-to-one.

| File | Shows |
|---|---|
| `sol-pi-teaser-hero-v17.png` | Page hero |
| `action-fusion.gif` | Action Fusion — two-lane before/after animation |
| `then-run-research-overview.svg` | Action Fusion: 4 research stages, 10 search points, counterfactual savings |
| `context-memory.gif` | Online Context Compact — compaction at subtask boundaries |
| `observation-pack.gif` | ObservationPack — handle substitution with exact recall |
| `observationpack-research-overview.png` | ObservationPack: 8-configuration sweep and paired EdgeBench A/B |
| `evidence-preserving-reducer.gif` | Evidence-Preserving Reducer — long log to verified receipt |
| `edgebench-performance.svg` | EdgeBench average score, native / Pi / SoL-Pi, both backends |
| `edgebench-cost.svg` | EdgeBench API-equivalent cost |
| `edgebench-total-tokens.svg` | EdgeBench total tokens |
| `terminal-bench-4-success.svg` | Terminal-Bench 4 tasks solved (18 / 18 / 15) |
| `terminal-bench-4-cost.svg` | Terminal-Bench 4 total cost ($272.35 / $286.45 / $211.12) |

```bash
mkdir -p blog && cd blog
BASE=https://nvlabs.github.io/SoL-Pi/assets

for f in \
  sol-pi-teaser-hero-v17.png \
  action-fusion.gif \
  then-run-research-overview.svg \
  context-memory.gif \
  observation-pack.gif \
  observationpack-research-overview.png \
  evidence-preserving-reducer.gif \
  edgebench-performance.svg \
  edgebench-cost.svg \
  edgebench-total-tokens.svg \
  terminal-bench-4-success.svg \
  terminal-bench-4-cost.svg
do
  curl -fsSL -o "$f" "$BASE/$f"
done
```

The four mechanism GIFs are ~14 MB together and dominate this directory's size;
drop them if the repo needs to stay light — the SVG/PNG research overviews carry
the numbers.

The page also offers a teaser video (`Download the SoL-Pi teaser video`) that is
not mirrored here.
