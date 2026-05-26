# SciLink

**LLM-powered agents for scientific research automation** — an AI research partner for
materials science, chemistry, physics, and adjacent experimental disciplines.

SciLink deploys a system of intelligent orchestrator agents that cover the full scientific
research cycle: plan experiments, analyze multi-modal instrument data, and run
computational simulations — all within a single, coherent session.

---

## Run

```bash
npx @open-gitagent/gitagent run -r https://github.com/ziatdinovmax/SciLink
```

---

## What It Can Do

SciLink provides three complementary orchestrator modes:

### 🔬 Analyze Mode
Multi-modal experimental data analysis powered by domain-specific skill bundles:
- **Microscopy & Image Analysis** — particle segmentation, grain mapping, SAM-powered feature extraction
- **Spectroscopy** — curve fitting, peak identification, XRD, Raman, EELS
- **Hyperspectral Datacubes** — 3D datacube analysis, dimensionality reduction, component mapping
- Generates and executes verified Python analysis code in a sandboxed environment
- Produces reproducible session artefacts (code, plots, structured findings)

### 📋 Plan Mode
Literature-grounded experimental campaign design:
- **Hypothesis Generation** — RAG over your papers, project notes, and prior results
- **Bayesian Optimization** — sequential single-objective and multi-objective BO for optimal next-experiment selection
- **Agentic Knowledge Query** — dynamically queries tabular databases and structured records without upfront schema definition
- Knowledge-only skill bundles (no runnable code) keep planning focused on reasoning and synthesis

### ⚛️ Simulate Mode
Computational modeling with iterative structure refinement:
- **DFT Workflows** — structure generation, VASP input preparation, INCAR validation against literature, post-run output analysis
- **Classical MD** — LAMMPS input generation, force-field selection, trajectory analysis
- **Structure Validation** — 3-axis visualizations, structure comparison, automated fix suggestions
- HPC job submission and result download via SSH/SLURM backend

### 🤖 Meta Orchestrator
A top-level router that delegates to the right specialist automatically — users interact with a single interface and never switch modes manually. Context and findings flow between specialists via a delegation ledger.

---

## Autonomy Levels

| Level | Behavior |
|---|---|
| **Co-Pilot** | Human reviews every step before the agent commits |
| **Autopilot** | Agent leads; human reviews major decisions and generated outputs |
| **Autonomous** | End-to-end execution, no human review — for headless/HPC pipelines |

---

## Skill Subsystem

Domain experts extend SciLink without touching core agent code by contributing self-contained
skill bundles: a `<name>.md` narrative file organized around a fixed section vocabulary
(`Overview → Planning → Implementation → Interpretation → Validation`) plus optional
Python helpers registered as tools. Skill-gated tool visibility keeps per-call context
focused on the active technique.

---

## Install

```bash
pip install scilink            # core (analysis + planning)
pip install scilink[ui]        # + Streamlit web UI
pip install scilink[sim]       # + simulation dependencies (ASE, atomate2, etc.)
pip install scilink[all]       # everything
```

Also available as an MCP server (`scilink mcp`) for integration with Claude Code and other MCP-compatible clients.

---

## Built with
[gitagent](https://github.com/open-gitagent/gitagent) — a git-native, framework-agnostic open standard for AI agents.
