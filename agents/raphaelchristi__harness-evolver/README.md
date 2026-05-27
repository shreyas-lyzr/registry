# Harness Evolver

**Harness Evolver** is a LangSmith-native autonomous agent optimizer for Claude Code. Point it at any LLM-based agent codebase and it will iteratively improve prompts, routing, tools, and architecture — automatically, with full evaluation-backed evidence for every change.

## What It Does

Harness Evolver runs an automated evolution loop on your AI agent:

1. **Sets up a LangSmith evaluation dataset** from your existing traces or test cases
2. **Spawns self-organizing proposer agents**, each investigating a data-driven lens (failing example patterns, routing issues, tool gaps)
3. **Tests each proposal** in an isolated git worktree — no risk to your main branch
4. **Evaluates with LangSmith** using LLM-as-judge with rubrics, pairwise comparison, and justification-before-score
5. **Gates regressions** — constraint checks, efficiency gates, Pareto selection, holdout enforcement
6. **Merges only winners** and builds cross-iteration memory to guide future proposals

## Key Capabilities

- **Multi-agent orchestration**: 6 specialized sub-agents (proposer, evaluator, critic, architect, consolidator, testgen)
- **30+ Python tools** for LangSmith integration, trace analysis, architecture analysis, regression tracking, and more
- **Evolution archive**: TF-IDF search over all past candidates (winners and losers) to avoid repeating failures
- **Self-abstention**: proposers honestly abstain when they can't add value
- **Secret detection**: all outputs filtered for API keys before logging
- **Compound learning**: proven evolution learnings are promoted back into CLAUDE.md

## Install

```bash
# Via Claude Code plugin marketplace (recommended)
/plugin marketplace add raphaelchristi/harness-evolver-marketplace
/plugin install harness-evolver

# Or via npx
npx harness-evolver@latest
```

## Quick Start

```bash
cd my-llm-project
export LANGSMITH_API_KEY="lsv2_pt_..."
claude

/harness:setup      # explores project, configures LangSmith
/harness:health     # check dataset quality
/harness:evolve     # runs the optimization loop
/harness:status     # check progress (rich ASCII chart)
/harness:deploy     # tag, push, finalize
```

## Real Results

Tested on a RAG agent (Agno framework, Gemini Flash Lite):

| Iteration | Score | Action |
|---|---|---|
| baseline | 0.575 | Original agent with hallucinations and broken tool calls |
| v002 | 0.950 | Breakthrough: inlined KB into prompt, eliminated vector search (5.7x faster) |
| v007 | 1.000 | One-shot example injection + rubric-aligned responses — perfect on held-out |

## Works With

Claude Code, Cursor, Codex, Windsurf

## Links

- [GitHub](https://github.com/raphaelchristi/harness-evolver)
- [npm](https://www.npmjs.com/package/harness-evolver)
- [Meta-Harness paper](https://arxiv.org/abs/2603.28052)
