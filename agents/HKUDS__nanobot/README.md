# nanobot

**nanobot** is an open-source, ultra-lightweight AI agent framework by [HKUDS](https://github.com/HKUDS). Inspired by Claude Code, OpenClaw, and Codex, it keeps the core agent loop small and readable while delivering production-grade capabilities across 13+ chat channels.

## What it does

nanobot runs a small, async agent loop that:
- Receives messages from **13+ chat platforms** — Telegram, Discord, Slack, WhatsApp, Feishu, Matrix, WeChat, WeCom, DingTalk, MS Teams, Email, WebSocket, and more
- Invokes **any LLM provider** — Anthropic, OpenAI, Azure, Bedrock, GitHub Copilot, Groq, Gemini, DeepSeek, and many more, with automatic fallback
- Executes **rich tools** — filesystem (read/write/edit), shell (with optional bubblewrap sandbox), web search & fetch, MCP servers, image generation, sub-agent spawning, and long-running goal tracking
- Persists **Dream memory** — two-phase consolidation so the agent carries context across sessions without token bloat

## Key capabilities

| Category | Details |
|---|---|
| **Channels** | Telegram, Discord, Slack, WhatsApp, Feishu, Matrix, WeChat, WeCom, DingTalk, MS Teams, Email, WebSocket |
| **Providers** | Anthropic, OpenAI, Azure, Bedrock, Copilot, Groq, Gemini, DeepSeek, OpenRouter, LM Studio, NIM, and more |
| **Tools** | Filesystem, shell, web search/fetch, MCP servers, image generation, sub-agents, cron, tmux |
| **Skills** | GitHub, weather, summarize, tmux, cron, long-goal, image-generation, memory, skill-creator |
| **Memory** | Dream two-phase consolidation, atomic session writes, context compaction |
| **API** | OpenAI-compatible HTTP API (`/v1/chat/completions`) + WebSocket multiplex |

## Example usage

```bash
# Install
pip install nanobot-ai

# Start the gateway (with Telegram, Discord, or Web UI)
nanobot gateway

# Sustained objective across sessions
/goal write a blog post about nanobot and publish it to my site

# Schedule a recurring task
/cron every monday at 9am: send me a standup summary
```

## Quick start

1. Install: `pip install nanobot-ai`
2. Configure: `nanobot setup` (interactive wizard)
3. Run: `nanobot gateway`
4. Connect your preferred channel (Telegram bot token, Discord webhook, etc.)

## Links

- **Docs**: https://nanobot.wiki
- **Repo**: https://github.com/HKUDS/nanobot
- **PyPI**: https://pypi.org/project/nanobot-ai/
- **Discord**: https://discord.gg/MnCvHqpUGB
