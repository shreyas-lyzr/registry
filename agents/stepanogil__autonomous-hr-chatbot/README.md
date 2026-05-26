# Autonomous HR Chatbot

An autonomous HR assistant agent that answers employee queries about HR policies,
leave balances, and employee data — no human in the loop required for routine
questions. Built by [@stepanogil](https://github.com/stepanogil).

## What it does

Employees ask natural-language questions and the agent:

1. **Checks timekeeping & leave policies** — retrieves the official HR policy document
   via vector search (Pinecone / OpenAI `file_search`) to answer questions about
   vacation, sick leave, overtime, public holidays, and encashment rules.
2. **Looks up personal employee data** — queries a structured employee database
   (CSV / pandas dataframe) for the authenticated user's remaining leave balances,
   supervisor, team, and other HR records.
3. **Calculates** — performs arithmetic for leave encashment values, pro-ration,
   and similar calculations.

## Key capabilities

- **ReAct-style agent loop** — thinks, picks the right tool, observes, repeats
  until it has a complete answer.
- **RAG over HR policy document** — no hallucinated policy details; always checks
  the source.
- **Two implementations shipped together:**
  - `root/` — classic 2023 LangChain + Pinecone + `gpt-3.5-turbo` version
  - `v2/` — 2026 rewrite using OpenAI Responses API directly (no LangChain, no
    Pinecone, `gpt-5.2` reasoning summaries, native `file_search` built-in)
- **Streamlit frontend** with chat interface, reasoning panel, and tool-trace UI.

## Example questions

```
"How many vacation leaves do I have left?"
"What is the policy on unused vacation leave?"
"If I encash 10 unused vacation days, how much will I be paid?"
"Who are the direct reports of Joseph Santos?"
"Can I apply for sick leave while on probation?"
```

## Tech stack

| Layer | Original (v1) | Modern (v2) |
|---|---|---|
| Model | `gpt-3.5-turbo` | `gpt-5.2` |
| Framework | LangChain | Pure OpenAI SDK |
| Vector DB | Pinecone | OpenAI file_search |
| Frontend | `streamlit-chat` | Native `st.chat_message` |

## Setup

Clone the repo, install requirements, add your OpenAI API key, and run:

```bash
# v2 (recommended)
cd v2 && pip install -r requirements.txt
python ingest_policy.py   # one-time: creates the vector store
streamlit run app.py
```

See the [repo README](https://github.com/stepanogil/autonomous-hr-chatbot#readme)
for full setup instructions, Azure OpenAI support, and Pinecone setup for v1.

## Links

- 📖 [Blog post walkthrough](https://medium.com/@stephen.bonifacio/creating-a-mostly-autonomous-hr-assistant-with-chatgpt-and-langchains-agents-and-tools-1cdda0aa70ef)
- 🎥 [Video demo](https://www.youtube.com/watch?v=id7XRcEIBvg)
