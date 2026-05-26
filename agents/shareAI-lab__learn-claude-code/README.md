# learn-claude-code

> **Bash is all you need** — A nano Claude Code–like agent harness, built from 0 to 1.

`learn-claude-code` is a 20-chapter, hands-on curriculum that teaches developers how to build production-grade Claude Code–style agent harnesses from first principles using the Anthropic Python SDK.

## What it does

Each of the 20 numbered chapters (`s01` → `s20`) ships a self-contained, runnable Python module that adds **exactly one new harness capability** on top of the previous one:

| Chapter | Capability |
|---------|-----------|
| s01 | Basic agent loop |
| s02 | Tool use (bash, read, write) |
| s03 | Permission governance |
| s04 | Hooks & observability |
| s05 | Todo/task tracking |
| s06 | Subagent spawning |
| s07 | Skill loading (on-demand SKILL.md) |
| s08 | Context compaction |
| s09 | Persistent memory |
| s10 | Runtime prompt assembly + caching |
| s11 | Error recovery & retries |
| s12 | Task graphs with dependency resolution |
| s13 | Background tasks |
| s14 | Cron scheduling |
| s15 | Agent teams |
| s16 | Async team protocols (mailbox) |
| s17 | Autonomous agents |
| s18 | Worktree isolation |
| s19 | MCP plugin integration |
| s20 | Comprehensive: all patterns combined |

## Key capabilities

- **Skills** — `agent-builder`, `code-review`, `mcp-builder`, `pdf`
- **Multilingual docs** — English, Chinese (中文), Japanese (日本語)
- **Zero framework dependencies** — pure Anthropic SDK + Python stdlib
- **62k+ GitHub stars** — one of the most-starred Claude Code reference repos

## Quick start

```bash
git clone https://github.com/shareAI-lab/learn-claude-code
cd learn-claude-code
pip install -r requirements.txt
cp .env.example .env  # add your ANTHROPIC_API_KEY + MODEL_ID
python s01_agent_loop/code.py
```

## GitAgent Protocol

This repo ships `agent.yaml` and `SOUL.md` at the root, making it runnable on any GAP-compatible runtime (Claude Code, GitClaw, and others).

The soul: *"You are a coding agent harness — not the agent itself, but the vehicle it rides in."*
