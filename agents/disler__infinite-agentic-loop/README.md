# Infinite Agentic Loop

**Orchestrate parallel Claude Code sub-agents in waves to generate evolving, unique content iterations — indefinitely.**

## What It Does

`infinite-agentic-loop` is a Claude Code slash-command agent (`/project:infinite`) that coordinates multiple sub-agents in parallel to produce spec-driven content iterations. It is both an architectural pattern and a working proof-of-concept for high-throughput, creative AI generation.

## Key Capabilities

- **Specification-driven generation** — reads a Markdown spec file to understand content format, naming conventions, quality standards, and creative constraints.
- **Directory reconnaissance** — inspects existing output before generating, ensuring every new iteration is unique and continues the trajectory.
- **Parallel sub-agent coordination** — deploys multiple Claude Code Task agents simultaneously:
  - 1–5 iterations → all at once
  - 6–20 iterations → batches of 5
  - `infinite` mode → successive waves of 3–5 agents until context limits are reached
- **Progressive sophistication** — each wave builds on the last, avoiding duplication while advancing creative evolution.

## Usage

```bash
# Start Claude Code in the repo
claude

# Then invoke the slash command
/project:infinite <spec_file> <output_dir> <count>

# Examples:
/project:infinite specs/invent_new_ui_v3.md src 1          # single
/project:infinite specs/invent_new_ui_v3.md src_new 5       # batch of 5
/project:infinite specs/invent_new_ui_v3.md src_new 20      # batch of 20
/project:infinite specs/invent_new_ui_v3.md infinite_src/ infinite  # forever
```

## Architecture

The agent is defined by two files in the repo root:

| File | Purpose |
|------|---------|
| `agent.yaml` | GAP manifest — model, runtime, skills, compliance |
| `SOUL.md` | Persona & instructions — orchestration philosophy and constraints |

The command logic lives in `.claude/commands/infinite.md` and is invoked through Claude Code's custom slash-command system.

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code/overview) installed and authenticated
- An Anthropic API key with sufficient context budget for parallel sub-agents

## Author

[disler](https://github.com/disler) — [IndyDevDan on YouTube](https://www.youtube.com/@indydevdan)
