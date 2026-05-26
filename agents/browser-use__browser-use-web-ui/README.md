# Browser Use Web UI

**Repo:** https://github.com/browser-use/web-ui  ·  ⭐ 16 000+  ·  MIT

A **Gradio web interface** for [browser-use](https://github.com/browser-use/browser-use)
that lets any LLM (OpenAI, Anthropic, Google Gemini, DeepSeek, Ollama, Mistral,
Azure OpenAI, and more) autonomously control a real Chromium browser.

---

## What it does

Give it a task in plain English. It figures out the browser actions needed —
clicking, typing, navigating, scrolling, extracting data — and executes them
step-by-step inside a live browser window you can watch in real time.

### Two agent modes

| Mode | Description |
|---|---|
| **Browser Agent** | Single-goal autonomous browsing. Give it a task; it completes it. |
| **Deep Research Agent** | Multi-tab, multi-step research orchestrated by LangGraph. Produces a cited Markdown report. |

---

## Key capabilities

- 🌐 **Multi-LLM** — plug in any LangChain-compatible model via `.env` or the Settings tab
- 🖥️ **Live browser view** — watch the agent work, pause/resume mid-task
- 🔐 **Own-browser support** — connect your existing Chrome profile so the agent inherits your logins
- 📹 **GIF recordings** — every session is recorded for audit/replay
- 🔌 **MCP tool support** — invoke Model Context Protocol tools mid-task
- 📝 **Persistent sessions** — keep the browser open between tasks (no re-login)
- 🐳 **Docker-ready** — ships a `Dockerfile` and `docker-compose.yml` for one-command deployment

---

## Quick start

```bash
git clone https://github.com/browser-use/web-ui.git && cd web-ui
cp .env.example .env          # add your LLM API key
uv pip install -r requirements.txt
playwright install chromium --with-deps
python webui.py --ip 127.0.0.1 --port 7788
# open http://127.0.0.1:7788
```

Or with Docker:

```bash
docker-compose up
```

---

## Example tasks

- *"Go to amazon.com and find the cheapest USB-C hub with at least 4 ports"*
- *"Research the top 5 open-source LLM frameworks released in 2024 and write a comparison report"*
- *"Fill in the contact form at example.com with my details and click Submit"*
- *"Scrape the pricing table from competitor.io and return it as JSON"*

---

## GitAgent Protocol

This agent ships `agent.yaml` + `SOUL.md` at the repo root, making it
GAP-conformant and runnable on any compatible runtime.  
Learn more at [gitagent.sh](https://gitagent.sh).
