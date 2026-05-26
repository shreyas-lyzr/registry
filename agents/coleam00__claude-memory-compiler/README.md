# claude-memory-compiler

> Give Claude Code a memory that evolves with your codebase.

**claude-memory-compiler** is an autonomous Claude Code agent that hooks into
your session lifecycle to silently capture, compile, and inject a growing
personal knowledge base — inspired by [Andrej Karpathy's LLM Knowledge Base
architecture](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f),
adapted for AI-assisted coding.

## What It Does

Every time you end a Claude Code session (or it auto-compacts), the agent:
1. **Captures** the conversation transcript via the `SessionEnd` / `PreCompact` hooks
2. **Extracts** decisions, lessons, patterns, and gotchas using the Claude Agent SDK (`flush.py`)
3. **Appends** a structured summary to today's daily log in `daily/YYYY-MM-DD.md`
4. **Compiles** daily logs into cross-referenced knowledge articles under `knowledge/` (nightly, or on demand)
5. **Injects** the knowledge-base index + recent log back into the next session via the `SessionStart` hook

The result: Claude always "remembers" your architecture decisions, preferred patterns, and hard-won lessons — without you having to re-explain them.

## Key Capabilities

| Script | What it does |
|---|---|
| `hooks/flush.py` | Extracts key knowledge from a session transcript via Claude Agent SDK |
| `scripts/compile.py` | Compiles daily logs into concept / connection / Q&A articles |
| `scripts/query.py` | Answers questions using index-guided retrieval (no RAG) |
| `scripts/lint.py` | Runs 7 health checks (broken links, orphans, contradictions, staleness) |

## Why No RAG?

Karpathy's insight: at personal scale (50–500 articles), an LLM reading a
structured `index.md` outperforms cosine similarity. No vector database, no
embeddings — just clean markdown and a master index.

## Quick Start

Tell your AI coding agent:

```
"Clone https://github.com/coleam00/claude-memory-compiler into this project.
Set up the Claude Code hooks so my conversations automatically get captured
into daily logs, compiled into a knowledge base, and injected back into future
sessions. Read the AGENTS.md for the full technical reference."
```

## Requirements

- Claude Code with a Max, Team, or Enterprise subscription (no separate API billing)
- Python 3.11+ with `uv`

## Architecture

```
Conversation
  → SessionEnd/PreCompact hooks
    → flush.py (Claude Agent SDK) extracts knowledge
      → daily/YYYY-MM-DD.md
        → compile.py → knowledge/concepts/, connections/, qa/
          → SessionStart hook injects index into next session
            → cycle repeats
```

## Repository

https://github.com/coleam00/claude-memory-compiler
