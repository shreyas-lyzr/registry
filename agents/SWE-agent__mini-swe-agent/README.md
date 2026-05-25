# mini-swe-agent

**The minimal AI software engineering agent.** Built by the Princeton & Stanford team behind [SWE-bench](https://github.com/swe-bench/SWE-bench) and [SWE-agent](https://github.com/SWE-agent/SWE-agent).

## What it does

`mini-swe-agent` solves GitHub issues and software engineering tasks by interacting with a computer **entirely through bash** — no custom tool implementations, no special interfaces, no complex scaffolding. Just the model, a shell, and a task.

Scores **>74% on SWE-bench Verified** with a ~100-line Python agent class.

## Key capabilities

- 🐚 **Bash-only** — no tool-calling interface required; works with any chat-completion model
- 🧩 **Model-agnostic** — runs on Claude, GPT-4, Gemini, and more via [litellm](https://github.com/BerriAI/litellm), OpenRouter, Portkey
- 📦 **Sandboxed** — local, Docker/Podman, Singularity/Apptainer, bubblewrap, contree
- 🔬 **Research-grade** — linear trajectory = perfect fine-tuning/RL data
- ⚡ **Fast startup** — starts much faster than heavier agent frameworks
- 🏢 **Production-adopted** — used by Meta, NVIDIA, Essential AI, IBM, Princeton, Stanford

## How it works

1. The agent receives a task (a GitHub issue or CLI prompt)
2. It reasons aloud in a THOUGHT block, then issues **one bash command**
3. The environment runs the command in a **fresh subshell** (stateless, safe)
4. The agent observes the output and iterates until the task is solved

```python
from minisweagent.agents.default import DefaultAgent
from minisweagent.models.litellm_model import LitellmModel
from minisweagent.environments.local import LocalEnvironment

agent = DefaultAgent(
    LitellmModel(model_name="claude-sonnet-4-5-20250929"),
    LocalEnvironment(),
)
agent.run("Write a sudoku game")
```

## Installation & usage

```bash
# Quickest — no install needed
pip install uv && uvx mini-swe-agent

# Or install permanently
pip install mini-swe-agent
mini  # run the CLI
```

## Benchmarks

| Model | SWE-bench Verified |
|---|---|
| Gemini 3 Pro | 74%+ |
| Claude Sonnet 4 | ~70% |
| GPT-5 | ~68% |

## Links

- 🌐 [Documentation](https://mini-swe-agent.com/latest/)
- 📄 [NeurIPS 2024 Paper](https://arxiv.org/abs/2405.15793)
- 🏆 [SWE-bench Leaderboard](https://www.swebench.com/)
- 💬 [Slack Community](https://join.slack.com/t/swe-bench/shared_invite/zt-36pj9bu5s-o3_yXPZbaH2wVnxnss1EkQ)
