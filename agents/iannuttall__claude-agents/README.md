# claude-agents

A curated library of **seven Claude Code custom sub-agents** by [@iannuttall](https://github.com/iannuttall), covering the full software-development lifecycle. Drop any agent into `.claude/agents/` and Claude Code automatically selects the right specialist for each task.

## Available agents

| Agent | What it does |
|---|---|
| **code-refactorer** | Improves code structure, readability, and maintainability without changing behaviour |
| **security-auditor** | Performs comprehensive security audits and produces prioritised remediation reports |
| **prd-writer** | Creates detailed, structured Product Requirements Documents |
| **project-task-planner** | Converts a PRD into a fully-phased development task list |
| **frontend-designer** | Translates mockups and wireframes into component specs and design systems |
| **content-writer** | Produces high-quality written content for a wide range of purposes |
| **vibe-coding-coach** | Translates app ideas and aesthetic preferences into working software |

## Installation

```bash
# Project-scoped
mkdir -p .claude/agents
cp agents/*.md .claude/agents/

# Global (all projects)
mkdir -p ~/.claude/agents
cp agents/*.md ~/.claude/agents/
```

## Usage

Once installed, Claude Code detects and delegates tasks to the appropriate agent automatically — no extra configuration needed.

## Links

- Repository: https://github.com/iannuttall/claude-agents
- License: MIT
