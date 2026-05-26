# smol developer

> *"Build the thing that builds the thing."*

**smol developer** is a human-centric AI junior developer agent that synthesises
entire codebases from a single natural-language product spec. Point it at what
you want to build, and it plans the architecture, maps out every file, and
generates fully-implemented, comment-annotated code — no stubs, no TODOs.

## What it does

1. **Plans** — given your prompt, it produces a GitHub-Markdown architecture plan
   naming every file, exported variable, DOM element ID, and function signature.
2. **Specifies** — uses structured function-calling to return the exact file list
   before writing a single line of code.
3. **Generates** — creates each file individually, in full, following the agreed
   plan. Raw valid source code only — no markdown fences, no placeholders.

## Key capabilities

- Full-program synthesis from one prompt (e.g. "a Pong game in HTML/JS/CSS")
- Pluggable model support — defaults to GPT-4o, works with GPT-3.5-turbo
- Streaming output with per-chunk callbacks
- Embeddable as a Python library (`smol_dev` package)
- Human-in-the-loop by design — you run the code and steer via prompt edits

## Example usage

```bash
pip install smol-developer
python main.py "a HTML/JS/CSS Tic Tac Toe game with AI opponent"
```

Or as a library:

```python
from smol_dev.main import main
main(prompt="a REST API in FastAPI with SQLite persistence")
```

## Links

- **Repository**: https://github.com/smol-ai/developer
- **Original launch**: https://twitter.com/swyx/status/1657578738345979905
- **GitAgent Protocol manifest**: `agent.yaml` + `SOUL.md` in the repo root
