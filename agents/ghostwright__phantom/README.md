# Phantom

> An AI co-worker with its own computer.

Phantom is a fully autonomous AI agent that runs as a persistent process on a dedicated VM. It is not a chatbot — it is a **colleague** that does real work, remembers everything, and gets measurably better over time through a self-evolution engine.

## What Phantom Does

- **Builds things**: APIs, dashboards, data pipelines, scripts, automations — without waiting for permission
- **Remembers everything**: Qdrant vector DB + SQLite give it episodic and semantic memory across sessions
- **Self-evolves**: After every session, it reflects, proposes config changes, and applies them through a validated evolution engine
- **Exposes itself as MCP**: 17+ tools available via a streamable HTTP MCP server at `/mcp` — other agents can delegate to it
- **Communicates everywhere**: Slack (primary), Web Chat, Telegram, Email, Webhook — same persistent identity across all channels
- **Collects credentials securely**: Encrypted at rest, never logged; it can onboard itself to new services on the fly

## Key Capabilities

| Capability | Detail |
|---|---|
| Model | Claude Opus 4.7 (default), swappable to any Anthropic-compatible endpoint |
| Memory | Qdrant (vectors) + SQLite (state, sessions, metrics) |
| Runtime | Bun + TypeScript, ~30,000 lines, 1,819 tests |
| Channels | Slack, Web Chat (SSE), Telegram, Email (IMAP/SMTP), Webhook |
| MCP Server | Streamable HTTP, bearer token auth, 17+ tools |
| Infrastructure | Docker Compose, Specter VMs (Hetzner), systemd |
| Self-Evolution | Reflection subprocess, versioned config, evolution log |

## Example: What a Production Phantom Has Actually Built

1. **Analytics Platform** — Installed ClickHouse, loaded 28.7M rows of Hacker News data, built a dashboard + REST API, then registered that API as an MCP tool for future agents.
2. **New Communication Channel** — When asked "Can I talk to you on Discord?", it explained the Discord Bot API, walked the user through creating an app, spun up a container, and went live. Nobody wrote code.
3. **Infrastructure Monitoring** — Found a 3-star open-source monitor (Vigil), integrated it into its ClickHouse instance, synced 890,450 rows of metrics, and built a self-monitoring dashboard.

## Getting Started

```bash
git clone https://github.com/ghostwright/phantom
cd phantom
cp .env.example .env    # fill in your keys
docker compose up       # pulls Qdrant + Ollama, starts Phantom
```

Then message your Phantom on Slack (or open `/chat` in your browser).

## Links

- 🌐 [Website](https://ghostwright.dev/phantom)
- 📦 [Docker Hub](https://hub.docker.com/r/ghostwright/phantom)
- 🐛 [Issues](https://github.com/ghostwright/phantom/issues)
- 📄 [License](https://github.com/ghostwright/phantom/blob/main/LICENSE) — Apache 2.0
