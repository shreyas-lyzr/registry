# Prompt-Factory

**Prompt-Factory** is a multi-agent pipeline that automatically generates enterprise-grade prompt suites for any AI system you want to build.

## What it does

Given a natural-language description of an AI product (e.g. "a coding assistant", "a customer-service bot", "a data-analysis agent"), Prompt-Factory coordinates five specialist agents in a quality-assured pipeline:

| Step | Agent | Responsibility |
|------|-------|---------------|
| 1 | **Analyzer** | Decomposes requirements into a multi-role architecture with roles, workflow, and quality gates |
| 2 | **Generator** | Produces complete, XML-structured prompts per role (identity, task, method, rules, examples, edge-cases) |
| 3 | **Reviewer** | Scores each prompt across 6 dimensions; flags weaknesses with severity ratings |
| 4 | **Optimizer** | Surgically fixes every flagged issue, targeting a quality score ≥ 8.0 / 10 |
| 5 | **Tester** | Designs functional, boundary, adversarial, and safety tests for the final suite |

## Key capabilities

- **End-to-end automation** — from a one-line description to a fully-tested, scored prompt suite
- **Iterative quality loops** — prompts below the quality threshold automatically cycle through optimisation
- **Bilingual** — prompt templates available in English and Chinese (`server/prompts/en/` and `server/prompts/cn/`)
- **REST API** — Flask-based server with pipeline, history, and settings endpoints
- **Vue 3 client** — browser UI for submitting requirements and inspecting results in real time
- **Persistent results** — all intermediate artefacts (architecture JSON, per-role prompts, review reports) saved to disk

## Example usage

```bash
# Start the backend
cd server && pip install -r requirements.txt && python run.py

# Start the frontend
cd client && npm install && npm run dev
```

Then open `http://localhost:5173`, describe the AI system you want prompts for, and let the pipeline run.

## Tech stack

- **Backend**: Python · Flask · OpenAI SDK
- **Frontend**: Vue 3 · TypeScript · Vite
- **Model**: OpenAI GPT-4o (configurable via settings)

## Links

- Repository: https://github.com/haneef1104/Prompt-Factory
- GitAgent Protocol PR: https://github.com/haneef1104/Prompt-Factory/pull/1
