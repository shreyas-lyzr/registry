# agents-deep-research

> A multi-agent deep research assistant powered by the [OpenAI Agents SDK](https://github.com/openai/openai-agents-python).

## What it does

**agents-deep-research** performs in-depth, iterative research on any topic and produces a comprehensive, well-cited Markdown report — autonomously, without asking clarifying questions.

It ships two research modes:

| Mode | Best for | Typical output |
|---|---|---|
| `IterativeResearcher` | Focused single-topic queries | Up to ~5 pages / 1 000 words |
| `DeepResearcher` | Structured, multi-section reports | 20+ pages with parallel section research |

## How it works

The agent pipeline runs in a loop:

1. **Knowledge Gap Agent** — analyses current research state and surfaces the next unknown.
2. **Tool Selector Agent** — decides which specialised agents to dispatch (web search, site crawler) and crafts precise 3-6 word queries.
3. **Tool Agents** — execute in parallel, returning structured findings with citations.
4. **Thinking / Observations Agent** — reflects on findings, notes contradictions, and steers the next loop iteration.
5. **Writer Agent** — synthesises everything into a final Markdown report with numbered URL citations.

For the `DeepResearcher`, a **Planner Agent** first creates a report outline, then parallel `IterativeResearcher` instances tackle each section, and a **Proofreader Agent** unifies the whole document.

## Key capabilities

- **Model agnostic** — works with OpenAI, Anthropic, Gemini, DeepSeek, Perplexity, OpenRouter, Azure OpenAI, Hugging Face, Ollama, LM Studio — any OpenAI-API-compatible model with structured output support.
- **Extensible tools** — custom tool agents can be added by dropping a file into `deep_researcher/agents/tool_agents/`.
- **Autonomous** — no mid-run clarifying questions; runs fully unattended.
- **Traced** — optional OpenAI trace monitoring per research session.
- **Installable** — available as `pip install deep-researcher`.

## Example usage

```bash
# Long-form structured report
deep-researcher --mode deep \
  --query "Comprehensive analysis of the EV battery supply chain" \
  --max-iterations 5 --max-time 20 --verbose

# Quick focused report
deep-researcher --mode simple \
  --query "Latest EU AI Act compliance requirements" \
  --max-iterations 3 --max-time 10 --output-length "3 pages"
```

```python
import asyncio
from deep_researcher import DeepResearcher, IterativeResearcher

# Structured multi-section report
researcher = DeepResearcher(max_iterations=5, max_time_minutes=20)
report = asyncio.run(researcher.run("Impact of quantum computing on cryptography"))

# Quick focused report
researcher = IterativeResearcher(max_iterations=3, max_time_minutes=5)
report = asyncio.run(researcher.run("UK renewable energy policy 2024-2025", output_length="2 pages"))
print(report)
```

## Links

- **Repository:** https://github.com/qx-labs/agents-deep-research
- **PyPI:** https://pypi.org/project/deep-researcher/
- **Author:** Jai Juneja @ [QX Labs](https://www.qxlabs.com)
- **License:** Apache-2.0
