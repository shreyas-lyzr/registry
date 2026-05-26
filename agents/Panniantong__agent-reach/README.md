# Agent Reach

> Give your AI agent eyes to see the entire internet.

**Agent Reach** is a unified CLI installer and routing layer that gives any shell-capable AI agent read/search access to 17+ internet platforms — **for free, with zero API fees**.

## What It Does

Instead of every developer individually wrestling with Twitter rate limits, Reddit 403s, YouTube auth, and Bilibili geo-blocks, Agent Reach solves it once:

- **One install**: `agent-reach install --env=auto` — sets up all tools automatically
- **One diagnose**: `agent-reach doctor` — tells you what works and what needs config
- **17+ platforms out of the box**:

| Platform | Capability |
|----------|-----------|
| 🐦 Twitter/X | Search tweets, read threads (cookie auth, free) |
| 📖 Reddit | Search posts, read threads + comments |
| 📺 YouTube | Transcript extraction, video search |
| 📦 GitHub | Repo reading, search, issues/PRs |
| 📺 Bilibili | Subtitle extraction + search |
| 📕 XiaoHongShu | Read notes, search, post, comment |
| 🎵 Douyin | Video parsing, watermark-free links |
| 💼 LinkedIn | Public profiles, job listings |
| 📰 Weibo | Hot search, user feeds, topics |
| 💬 WeChat Articles | Full-text Markdown extraction |
| 💻 V2EX | Hot posts, node posts, replies |
| 📈 Xueqiu | Stock quotes, hot posts |
| 📡 RSS | Any RSS/Atom feed |
| 🌐 Web | Any URL via Jina Reader |
| 🔍 Search | Semantic web search via Exa |
| 🎙️ Podcasts | Audio-to-text via Whisper (Xiaoyuzhou) |
| 🏢 Boss直聘 | Job listings |

## How It Works

Agent Reach is a **glue layer**, not a scraper. It installs best-in-class open-source CLI tools (twitter-cli, rdt-cli, yt-dlp, Jina Reader, Exa, mcporter) and configures them. Agents call the upstream tools directly — Agent Reach stays out of the critical path.

## Quick Start

```bash
# Install Agent Reach
pip install agent-reach

# Auto-configure all tools
agent-reach install --env=auto

# Check what's working
agent-reach doctor

# Read any URL
agent-reach read https://example.com

# Search Twitter
agent-reach search-twitter "query"
```

Or just paste this to your AI agent:
```
Help me install Agent Reach: https://raw.githubusercontent.com/Panniantong/agent-reach/main/docs/install.md
```

## Compatibility

Works with **any shell-capable AI agent**: Claude Code, OpenClaw, Cursor, Windsurf, Codex, and more. Supports MCP via mcporter.

## Key Design Principles

- 💰 **100% free** — no paid API keys required for any core feature
- 🔒 **Privacy-preserving** — cookies stay local, nothing uploaded
- 🔄 **Maintained** — upstream tool updates tracked continuously
- 🩺 **Self-diagnosing** — built-in doctor command for troubleshooting

## Links

- 📦 [GitHub Repository](https://github.com/Panniantong/Agent-Reach)
- 📖 [English README](https://github.com/Panniantong/Agent-Reach/blob/main/docs/README_en.md)
- 🐦 [Author Twitter](https://x.com/Neo_Reidlab)
