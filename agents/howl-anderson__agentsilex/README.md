# AgentSilex

**A transparent, minimal, and hackable Python agent framework — ~300 lines of readable core code.**

> "Read the entire codebase in one sitting. Understand exactly how your agents work. No magic, no hidden complexity."

## What It Does

AgentSilex is a general-purpose AI agent framework designed for developers who want full control over their agent's behaviour. Unlike large frameworks that become black boxes, AgentSilex exposes every decision point and makes it trivially easy to customise.

Built on [LiteLLM](https://github.com/BerriAI/litellm), it works with **100+ LLM providers out of the box** — switch from Anthropic to OpenAI to DeepSeek with a single string change.

## Key Capabilities

| Capability | Details |
|---|---|
| **Universal LLM support** | OpenAI, Anthropic, Google Gemini, DeepSeek, Azure, Mistral, local models via LiteLLM |
| **Tool Calling** | `@tool` decorator — auto-extracts schema from type hints & docstrings |
| **Multi-Agent Handoffs** | Route requests to specialist sub-agents with `handoffs=[...]` |
| **Agents as Tools** | Wrap any agent as a tool with `.as_tool()` |
| **Structured Output** | Pydantic model responses, type-safe and validated |
| **MCP Client** | Connect to Model Context Protocol servers for external tool access |
| **Streaming** | Real-time events: `PartialOutputEvent`, `ToolCallEvent`, `FinalResultEvent` |
| **Agent Memory** | Callback-based history management (summarise, truncate, inject context) |
| **Observability** | Built-in OpenTelemetry tracing, compatible with Phoenix and any OTLP backend |
| **Evaluation** | Tool-trajectory matching, ROUGE, and LLM-as-judge scoring |

## Quick Start

```python
from agentsilex import Agent, Runner, Session, tool

@tool
def get_weather(city: str) -> str:
    """Get weather for a city."""
    return "SUNNY"

agent = Agent(
    name="Weather Assistant",
    model="anthropic/claude-3-5-sonnet",   # or openai/gpt-4o, google/gemini-2.0-flash ...
    instructions="Help users find weather information.",
    tools=[get_weather]
)

result = Runner(Session()).run(agent, "What's the weather in Paris?")
print(result.final_output)
```

## Multi-Agent Example

```python
main_agent = Agent(
    name="Orchestrator",
    model="openai/gpt-4o-mini",
    instructions="Route questions to the right specialist.",
    handoffs=[weather_agent, faq_agent],
)
```

## Installation

```bash
pip install agentsilex
# or
uv add agentsilex
```

## Why AgentSilex in the GAP Registry?

AgentSilex embodies the GitAgent Protocol's philosophy: portable, inspectable, hackable agents that anyone can run on any compatible runtime. With its universal LLM support and minimal architecture, an AgentSilex agent can be defined once in `agent.yaml` + `SOUL.md` and deployed across any GAP-compatible runtime.

## Links

- **GitHub**: https://github.com/howl-anderson/agentsilex
- **PyPI**: https://pypi.org/project/agentsilex/
- **GitAgent Protocol**: https://gitagent.sh
