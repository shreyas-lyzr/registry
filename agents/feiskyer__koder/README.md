# Koder

**Koder** is an open-source, terminal-first AI coding assistant built in Python.
It combines a streaming Rich TUI, persistent local sessions, repository-aware
tools, extensible skills, Model Context Protocol (MCP) integrations, and
multi-agent workflows in a single runtime.

## Key Capabilities

- **Multi-provider LLM routing** — OpenAI, Anthropic, Google/Gemini, Azure, GitHub
  Copilot, OpenRouter, and 100+ LiteLLM providers. Set `KODER_MODEL` and go.
- **Persistent local sessions** — conversations, memories, tasks, and settings are
  stored in SQLite under `~/.koder/`. Nothing leaves your machine without explicit
  configuration.
- **Repository-aware tools** — file read/write/edit, glob/grep search, shell
  execution with git helpers, web search/fetch, and notebook editing.
- **Extensible runtime** — add project or user skills, plugins, MCP servers, and
  channels to grow Koder's capabilities without modifying the core.
- **Multi-agent workflows** — delegate tasks to background subagents, run local
  teams (in-process or tmux), route via mailboxes, and coordinate with task records.
- **Permission system** — configurable permission rules, sandbox policy, workspace
  roots, and approval hooks ensure destructive actions require explicit sign-off.

## Quick Start

```bash
uv tool install koder
export KODER_API_KEY="your-api-key"
export KODER_MODEL="gpt-4o"
koder
```

Or install from source:

```bash
git clone https://github.com/feiskyer/koder.git
cd koder
uv sync
uv run koder
```

## Example Usage

```bash
# Interactive session
koder

# Single prompt
koder "Refactor the login module to use async/await"

# Named session (resumable)
koder -s my-feature "Add pagination to the user list endpoint"

# Resume the last session
koder --resume
```

## Tool Categories

| Category | Tools |
|----------|-------|
| File     | `read_file`, `write_file`, `append_file`, `edit_file`, `list_directory`, `notebook_edit` |
| Search   | `glob_search`, `grep_search` |
| Shell    | `run_shell`, `shell_output`, `shell_kill`, `git_command` |
| Web      | `web_search`, `web_fetch` |
| Task     | `task_delegate`, `todo_read`, `todo_write` |
| Skills   | bundled skills, plugin skills, MCP resources |

## GitAgent Protocol

Koder ships with `agent.yaml` and `SOUL.md` at the repo root, making it fully
GAP-compliant. It can be loaded by any GAP-compatible runtime.

## Links

- **Repository**: https://github.com/feiskyer/koder
- **PyPI**: https://pypi.org/project/koder/
- **License**: MIT
