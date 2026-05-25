# SkillForge

**SkillForge** is an AI agent that generates production-grade Agent Skill packages through a structured, multi-step pipeline — aligned with the Anthropic Agent Skills specification. Give it a skill name and description; it outputs a complete, immediately usable skill directory.

## What It Does

SkillForge runs a 7-step pipeline to forge each skill from scratch:

| Step | Name | Output |
|------|------|--------|
| 1 | Requirement deep analysis | Structured requirements doc (2,000–5,000 chars) |
| 2 | Architecture decisions | Structure pattern, freedom level, resource file plan |
| 3 | Metadata crafting | Scored YAML frontmatter with optimized `description` |
| 4 | SKILL.md body generation | Core skill file, 150–450 lines, with ❌/✅ examples |
| 5 | Quality audit | 10-dimension scorecard; auto-rewrites anything < 8/10 |
| 6 | Resource file generation | `scripts/`, `references/`, `templates/` per the plan |
| 7 | Usage documentation | Trigger examples, install instructions, checklist |

It also supports a 3-step **fix mode**: diagnose an existing skill, rewrite it to best practices, audit the rewrite.

## Key Capabilities

- **One-click generation** — input a skill name + description, get a complete skill package
- **Fix & optimize** — upload an existing SKILL.md, get a best-practices rewrite
- **Real-time streaming** — each pipeline step streams its output live in the web UI
- **Marker-based extraction** — uses `%%SKILL_BEGIN%%` / `%%SKILL_END%%` to prevent truncation
- **ZIP download** — one-click download of the complete skill directory, ready to install
- **Task control** — cancel running tasks, retry failed steps, delete history

## Tech Stack

| Layer | Technology |
|-------|------------|
| Frontend | React 19 + Tailwind CSS 4 + shadcn/ui |
| Backend | Express 4 + tRPC 11 |
| Database | MySQL / TiDB (Drizzle ORM) |
| LLM | Claude CLI / Anthropic API / OpenAI-compatible |

## Example Usage

```
User: "Create a skill called 'docker-deploy' that helps agents deploy Docker containers to production"

→ SkillForge runs 7 steps, produces:
   docker-deploy/
   ├── SKILL.md           (150–450 lines, fully validated)
   ├── scripts/validate.sh
   └── references/deployment-patterns.md
```

## Installation

```bash
git clone https://github.com/mmlong818/skillforge.git
cd skillforge
pnpm install
cp .env.example .env   # configure DB + LLM backend
pnpm db:push
pnpm dev
```

See the [README](https://github.com/mmlong818/skillforge) for full setup instructions.

## Core Design Principles

SkillForge enforces these principles on every skill it generates:

- **Concise is key** — include only what the AI model doesn't already know
- **Description is the trigger** — must encode WHAT + WHEN to maximize selection accuracy
- **Progressive disclosure** — SKILL.md under 500 lines; heavy content in `references/`
- **Code > text** — runnable examples over verbose descriptions
- **Anti-patterns are essential** — ❌/✅ contrast format for every common mistake
