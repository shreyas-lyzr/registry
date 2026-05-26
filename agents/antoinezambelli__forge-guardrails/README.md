# forge-guardrails

**A reliability layer for self-hosted LLM tool-calling.**

Forge takes an 8B local model from single-digit pass rates to **84% across a
26-scenario eval suite** — and lifts Claude Sonnet from 85% to 98% on the same
workload — by applying composable guardrails without changing a single line of
your agent code.

## What it does

Forge intercepts model responses before they reach your client or downstream
logic and applies (in order):

1. **Response validation** — every tool call is checked against the declared `tools` array; unknown names and malformed shapes are caught before surfacing.
2. **Rescue parsing** — Mistral `[TOOL_CALLS]`, Qwen `<tool_call>` XML, and fenced JSON are normalised to the canonical OpenAI `tool_calls` schema.
3. **Retry with error tracking** — on validation failure, forge retries inference with a corrective tool-result message (up to `max_retries`, default 3).
4. **Synthetic `respond` tool injection** — prevents small models from breaking the tool-calling loop by routing plain-text responses through a structured call (stripped from the outbound response so the client never sees it).

## Three usage modes

| Mode | How | Best for |
|------|-----|----------|
| **Proxy server** | `python -m forge.proxy` | Drop-in for existing clients (opencode, aider, Claude Code, Continue) |
| **WorkflowRunner** | Python API | Building new agentic loops directly on forge |
| **Guardrails middleware** | `Guardrails` facade | Adding forge's stack inside your own orchestration loop |

## Supported backends

Ollama · llama-server (llama.cpp) · Llamafile · vLLM · Anthropic API

## Quick install

```bash
pip install forge-guardrails                    # core
pip install "forge-guardrails[anthropic]"       # + Anthropic client
```

## Claude Code integration

Point Claude Code at a forge-guarded local model:

```bash
python -m forge.proxy --backend llamaserver --gguf path/to/model.gguf --port 8081
# then:
ANTHROPIC_BASE_URL=http://localhost:8081 ANTHROPIC_AUTH_TOKEN=anything claude
```

## Eval harness

```bash
python -m tests.eval.eval_runner --backend llamafile --gguf path/to/model.gguf --runs 10
python -m tests.eval.report eval_results.jsonl
```

## Links

- Repository: https://github.com/antoinezambelli/forge
- PyPI: https://pypi.org/project/forge-guardrails/
- Paper: https://doi.org/10.1145/3786335.3813193
- Docs: https://github.com/antoinezambelli/forge/tree/main/docs
