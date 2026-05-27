# Memora

> *"You never truly know the value of a moment until it becomes a memory."*

**Memora** is a lightweight [MCP (Model Context Protocol)](https://github.com/modelcontextprotocol) server that gives AI agents **persistent memory** across sessions.

## What it does

Instead of losing context when a session ends, agents that use Memora can store, retrieve, and reason over memories that persist indefinitely in a local SQLite database (with optional cloud sync to S3, Cloudflare R2, or D1).

## Key capabilities

| Feature | Detail |
|---------|--------|
| **Persistent storage** | SQLite, exportable, optional cloud sync |
| **Semantic search** | TF-IDF · sentence-transformers · OpenAI embeddings |
| **Knowledge graph** | Typed edges, cluster detection, interactive visualiser |
| **LLM deduplication** | Find + merge near-duplicates with confidence scores |
| **Memory insights** | Activity summaries, stale alerts, pattern analysis |
| **Document storage** | Markdown → searchable fragment trees (claims, risks, plans) |
| **Multi-agent events** | Poll-based inter-agent notification system |
| **Structured types** | First-class TODO, issue, and section memory kinds |

## Quick start

```bash
pip install git+https://github.com/agentic-box/memora.git
```

Add to your `.mcp.json`:

```json
{
  "mcpServers": {
    "memora": {
      "command": "memora-server",
      "args": [],
      "env": { "MEMORA_DB_PATH": "~/.local/share/memora/memories.db" }
    }
  }
}
```

## GAP integration

Memora ships with a fully valid `agent.yaml` manifest and `SOUL.md` persona file,
making it compatible with any GAP-aware runtime out of the box.

- **Adapters:** `claude-code`, `mcp`, `system-prompt`
- **Model:** `anthropic:claude-sonnet-4-6`
- **Transport:** stdio (default) · streamable-http

## Links

- [GitHub](https://github.com/agentic-box/memora)
- [Registry entry PR](https://github.com/open-gitagent/registry)
