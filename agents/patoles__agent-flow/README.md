# Agent Flow

**Real-time visualization of Claude Code and Codex agent orchestration.**

Agent Flow makes the invisible visible. When you run a Claude Code or Codex session, you don't see *how* the agent thinks — you just get the result. Agent Flow renders every tool call, subagent spawn, branching decision, and return flow as an interactive node graph, streamed live as your agent works.

Created by [Simon Patole](https://github.com/patoles) while building [CraftMyGame](https://craftmygame.com), where debugging AI agent behavior was painful enough to solve properly.

---

## Key Capabilities

- **Live node graph** — Visualize agent execution as an interactive, pannable/zoomable canvas. Each node is a tool call or subagent; edges show data flow and branching.
- **Claude Code hooks** — Auto-configures a lightweight HTTP hook server to receive events directly from Claude Code with zero latency.
- **Codex rollout tailing** — Reads `~/.codex/sessions/**/rollout-*.jsonl` and surfaces tool calls, reasoning steps, and token counts from Codex's own event stream.
- **Multi-session tabs** — Track multiple concurrent agent sessions side-by-side, tagged by runtime (`claude` / `codex`).
- **Timeline + transcript panels** — See where time was spent, which files were touched (file attention heatmap), and the full message transcript.
- **JSONL replay** — Point Agent Flow at any `.jsonl` event log to replay or watch a historical run.
- **Zero intrusion** — Agent Flow only observes; it never modifies your agent, prompts, or files.

## Interfaces

| Interface | Command |
|---|---|
| Standalone (quickest) | `npx agent-flow-app` |
| Web app (from source) | `git clone` → `pnpm i && pnpm run dev` |
| VS Code Extension | Install → `Cmd+Shift+P` → "Agent Flow: Open Agent Flow" |

## Runtime Support

Set `agentVisualizer.runtime` (VS Code) or `AGENT_FLOW_RUNTIME` env var to `claude`, `codex`, or `auto` (default: both).

## Requirements

- Node.js 20+ / pnpm
- Claude Code CLI and/or Codex
- VS Code 1.85+ (for the extension)

## License

Apache 2.0 — [github.com/patoles/agent-flow](https://github.com/patoles/agent-flow)
