# claude-code-agents

A complete E2E development workflow for solo developers building with Next.js +
Claude Code. Gives a single engineer the full leverage of a QA team, code
reviewer, DevOps engineer, and security analyst — all via Claude Code subagents
with strict, non-overlapping scopes.

Built by Paul @ [UndeadList](https://undeadlist.com).

## What It Does

Orchestrates **24 specialised subagents** across five categories:

| Category | Agents | Run Mode |
|----------|--------|----------|
| **Audit** (11) | bug, code-quality, security, docs, infra, UI/UX, database, performance, dependencies, SEO, API | Parallel |
| **Fix/Implement** (4) | fix-planner, code-fixer, test-runner, test-writer | Sequential |
| **Browser QA** (4) | browser-qa-agent, fullstack-qa-orchestrator, console-monitor, visual-diff | Mixed |
| **Deploy** (2) | deploy-checker, env-validator | Sequential |
| **Utility & Supervision** (3) | pr-writer, seed-generator, architect-reviewer | On-demand |

## Workflow Skills

Six slash-command workflows are available when installed as a Claude Code plugin:

| Skill | Purpose |
|-------|---------|
| `/full-audit` | Spawns all 11 auditors in parallel → fix-planner |
| `/pre-commit` | Bug + code-quality + security gate |
| `/pre-deploy` | Full pre-deployment validation |
| `/new-feature` | Plan → implement → QA loop |
| `/bug-fix` | test-writer → code-fixer → test-runner |
| `/release-prep` | Full audit + fixes + deploy-checker + pr-writer |

## Key Design Principles

- **Single security authority** — only `security-auditor` writes security findings; no overlap
- **Mandatory status blocks** — every agent response opens with a YAML status block (`COMPLETE | PARTIAL | SKIPPED | ERROR`) for pipeline visibility
- **Human-in-the-loop on destructive ops** — destructive changes require explicit confirmation
- **`.env` is untouchable** — environment secrets are never modified

## Installation

```bash
# Install as a Claude Code plugin (recommended — works across all projects)
cat .claude-plugin/plugin.json

# Or copy into a specific project
./setup-project.sh
```

## Target Stack

Next.js / React / TypeScript · Prisma · npm/pnpm · Vercel

Other stacks can adapt the agent prompt files in `agents/`.

## Links

- [GitHub Repository](https://github.com/undeadlist/claude-code-agents)
- [GitAgent Protocol](https://gitagent.sh)
