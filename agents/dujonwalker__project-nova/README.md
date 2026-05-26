# Project NOVA — Networked Orchestration of Virtual Agents

**Project NOVA** is a comprehensive, self-hosted multi-agent AI assistant ecosystem that
routes every user request to the right specialist through an intelligent hub-and-spoke
architecture powered by n8n, MCP servers, and an OpenWebUI chat frontend.

## What it does

A central **Router Agent** analyses each incoming message and dispatches it to one of
25+ domain-specific sub-agents, each backed by a dedicated MCP server running in Docker:

| Domain | Agents |
|---|---|
| Knowledge Management | TriliumNext, Blinko, BookStack, Memos, Outline, SiYuan, Karakeep, Paperless, OnlyOffice |
| Development & Repos | CLI Server, Forgejo, Gitea, System Search |
| Media & Creative | Ableton Copilot, OBS, REAPER, REAPER QA, YouTube Transcript |
| AI & Automation | Flowise, Langfuse, Puppeteer, RAGFlow, Fetch |
| Monitoring & Home | Home Assistant, Prometheus |

## Key capabilities

- **Intelligent routing** — the router reads conversation history, recognises service
  names, and dispatches to the right expert without asking unnecessary questions.
- **25+ MCP servers** — every sub-agent is backed by a containerised MCP server;
  Dockerfiles and docker-compose files are included for easy self-hosting.
- **n8n orchestration** — n8n workflow JSON files handle the plumbing between the
  OpenWebUI frontend, the router, and the sub-agents.
- **Privacy-first** — everything runs locally; no data leaves your infrastructure.
- **Extensible** — add new agents using the included prompt and container templates.

## Example queries

```
"Search my TriliumNext notes for the project kick-off meeting notes"
→ routed to: triliumnext-agent

"Is the living room light on?"
→ routed to: home-assistant-agent

"Get the transcript of https://youtube.com/watch?v=..."
→ routed to: youtube-agent

"Create a new track in my REAPER project"
→ routed to: reaper-agent
```

## Architecture

```
OpenWebUI  →  n8n workflow  →  Router Agent  →  Sub-Agent (MCP)
                                                      ↓
                                               Tool call result
                                                      ↓
                                          Response returned to user
```

## Getting started

See the [full README and reference guide](https://github.com/dujonwalker/project-nova)
for Docker setup, n8n workflow import, and per-agent configuration.
