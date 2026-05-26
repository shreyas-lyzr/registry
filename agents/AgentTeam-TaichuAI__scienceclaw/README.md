# ScienceClaw

**ScienceClaw** is a self-hosted, privacy-first personal research assistant built on
[LangChain DeepAgents](https://github.com/langchain-ai/deepagents) and the AIO Sandbox.
It performs rigorous multi-source deep research and generates professional PDF/DOCX reports —
entirely on your own machine, with every step visible and traceable.

## What it does

Given any research question, ScienceClaw:

1. **Decomposes** the question into investigation dimensions
2. **Plans data sources** — academic literature (arXiv, PubMed, OpenAlex, Semantic Scholar …) + ToolUniverse scientific databases + web search
3. **Collects** data in parallel across all planned sources
4. **Cross-analyses** findings and synthesises them around the original question
5. **Generates** a professional research report as PDF and/or DOCX

## Key capabilities

- **1,900+ scientific tools** via ToolUniverse across multiple disciplines:
  - 💊 Drug discovery & biomedicine (UniProt, OpenTargets, FAERS, PDB, AlphaFold, ADMET)
  - 🔭 Astronomy & space science (SIMBAD, SDSS, NASA exoplanet archive, JPL Horizons)
  - 🌍 Earth & environmental science (USGS, ERDDAP, SoilGrids, air quality)
  - ⚗️ Chemistry & materials (COD crystal structures, molecular property prediction)
  - 🌱 Biodiversity (GBIF, OBIS, POWO, WoRMS, eBird)
  - 📊 Social science & statistics (World Bank, Eurostat, US Census, Wikidata)
  - 📚 Academic literature (PubMed, arXiv, OpenAlex, Semantic Scholar, DBLP, Crossref)
- **Composable skill system** — deep-research, brainstorming, copywriting, GitHub reading, weather, writing plans
- **Custom tool extension** — drop `@tool`-decorated Python into `Tools/`; hot-loaded without restart
- **Natural-language tool creation** — describe what you need; ScienceClaw writes, tests, and saves it
- **Full transparency** — every tool call and reasoning step is shown in the UI
- **Completely local** — Docker-isolated, nothing uploaded externally

## Example usage

> *"Summarise the current state of BRCA1 inhibitors in triple-negative breast cancer, including clinical trial status and key resistance mechanisms."*

ScienceClaw queries OpenTargets for BRCA1 targets, searches PubMed/arXiv for recent literature, retrieves FAERS adverse-event data, runs web search for trial updates, cross-analyses all sources, and produces a multi-section PDF report with citations.

## Quick start

```bash
git clone https://github.com/AgentTeam-TaichuAI/ScienceClaw.git
cd ScienceClaw
docker compose -f docker-compose-release.yml up -d --pull always
# Open http://localhost:5173
```

## Links

- Repository: https://github.com/AgentTeam-TaichuAI/ScienceClaw
- Cloud demo: https://scienceclaw.zidongtaichu.com/
- GitAgent Protocol manifest: `agent.yaml` + `SOUL.md` at repo root
