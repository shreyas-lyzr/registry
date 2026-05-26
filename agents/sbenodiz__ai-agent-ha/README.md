# AI Agent HA

A Home Assistant custom integration that connects your smart home to any major AI provider
through a clean, embedded chat interface. Talk to your home in plain English — no YAML, no
entity IDs, no card-type look-ups needed.

## What it does

**Device control** — Turn lights on/off, set brightness and colour temperature, adjust
thermostats, open/close covers, trigger scenes, and call any Home Assistant service directly
from the chat.

**Smart queries** — Ask about the current state of any entity, fetch historical sensor data,
get weather forecasts, or browse your area and device registries.

**Automation creation** — Describe what you want ("turn on the garden lights at sunset when
someone is home") and the agent composes a valid HA automation for you to review. One click
creates it in your instance.

**Dashboard building** — Request a dashboard by purpose ("create a security dashboard with
all door sensors and cameras") and the agent discovers the right entities, picks appropriate
Lovelace card types, and adds the finished dashboard to your sidebar.

## Supported AI providers

OpenAI (GPT-4, GPT-3.5), Anthropic (Claude Sonnet, Claude Opus), Google Gemini
(2.5 Flash, 2.5 Pro), OpenRouter, Meta Llama, z.ai (GLM), local Ollama, and any
OpenAI-compatible endpoint.

## Installation

Install via HACS (one click) or manually drop the `custom_components/ai_agent_ha` folder
into your HA config directory. Configure your preferred AI provider and API key in the
integration UI, then open the AI Agent HA panel in your sidebar.

## Key capabilities

- Natural-language smart-home control across all HA domains
- Automation generation with human-in-the-loop confirmation before creation
- Lovelace dashboard generation with intelligent entity discovery
- Multi-provider model support — swap providers without changing anything else
- Secure credential storage (API keys never appear in logs or chat)
- Conversational clarification — the agent asks follow-up questions when your request is ambiguous

## Example interactions

```
"Turn off all the lights on the ground floor"
"Create an automation that runs the dishwasher at midnight on weekdays"
"Show me the temperature history for the living room over the last 24 hours"
"Build an energy monitoring dashboard with power usage graphs"
```

## Links

- Repository: https://github.com/sbenodiz/ai_agent_ha
- HACS install: https://my.home-assistant.io/redirect/hacs_repository/?owner=sbenodiz&repository=ai_agent_ha&category=integration
- Issues: https://github.com/sbenodiz/ai_agent_ha/issues
