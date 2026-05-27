# abstract-agent

A **fully local, 100% private** multi-agent research system for generating novel
academic hypotheses and publication-ready abstracts. No API keys. No cloud.
Just you, your GPU/CPU, and Ollama.

## What it does

Given a research topic, abstract-agent orchestrates a five-stage agent pipeline
that searches real literature databases, critiques existing work, synthesises new
directions, generates a bold hypothesis, polishes it into a publication-ready
abstract, and scores its novelty — all on your own hardware.

## Key capabilities

- **Multi-source literature search** — pulls from arXiv, Semantic Scholar,
  PubMed, bioRxiv, medRxiv, EuropePMC, Crossref, DOAJ, and OpenAlex
- **Five specialised sub-agents:**
  - **Agent A · Breakdown** — decomposes the topic with encyclopedic thoroughness
  - **Agent B · Critique** — identifies gaps, contradictions, and over-explored areas
  - **Agent C · Synthesis** — integrates feedback into a refined research direction
  - **Agent D · Novelty Generation** — proposes one bold, unconventional hypothesis
  - **Agent E · Academic Structuring** — produces a single-paragraph publication-ready abstract
- **Novelty Assessment** — scores the hypothesis (1–10) against retrieved literature
- **Run stats** — reports papers searched/used, total time taken
- **Config-driven** — swap models, change personas, extend the pipeline via `agents_config.yaml`
- **Zero data egress** — all LLM calls go to your local Ollama instance

## Example output

```
Novelty Score: 7/10

Hypothesis: This research introduces a novel approach to LLM compression 
predicated on Neuro-Symbolic Contextual Compression, translating attention 
maps into a discrete graph representation and employing learned graph pruning 
to preserve critical semantic relationships while reducing model size.
```

## Quickstart

```bash
git clone https://github.com/tegridydev/abstract-agent
cd abstract-agent
pip install -r requirements.txt
ollama pull gemma3:4b
python agent/agent.py
```

## Configuration

Edit `agent/agents_config.yaml` to change:
- Ollama model (default: `gemma3:4b`)
- Agent personas and prompt templates
- Number of literature sources fetched
- Pipeline steps and output fields

## Requirements

- Python 3.9+
- [Ollama](https://ollama.com/download) running locally
- Internet access for public literature APIs (read-only)

## License

MIT — built by [tegridydev](https://github.com/tegridydev). Fork it, break it, share it.
