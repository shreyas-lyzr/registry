# agent-redteam

A Claude-powered **Agentic LLM Red Team Harness** by Fajar Sajid (Purdue University) that systematically probes AI agent system prompts for identity abuse, credential exfiltration, privilege escalation, and safety boundary vulnerabilities — and maps findings to MITRE ATT&CK.

---

## Run

```bash
npx @open-gitagent/gitagent run -r https://github.com/fajarsajid/agent-redteam
```

---

## What It Does

`agent-redteam` gives you a security analyst powered by Claude that attacks your agent's system prompt the way a real adversary would — before they get the chance.

Point it at any system prompt file and it generates tailored adversarial probes across 8 attack categories, evaluates whether each probe would succeed, scores every finding on a CVSS-like scale, and produces both a human-readable Markdown incident report and machine-readable JSON for SIEM or CI pipeline integration.

---

## Key Capabilities

- **Adversarial Probe Generation** — Claude crafts realistic, targeted probes specific to the content of your system prompt (its tools, permissions, and stated constraints) — not generic toy examples
- **8 MITRE-Mapped Attack Categories** — covers Prompt Injection (Direct & Indirect), Identity Spoofing, Goal Hijacking, Privilege Escalation, Data Exfiltration, Credential Exfiltration, and Safety Boundary Bypass
- **5 Failure Mode Detection** — Instruction Override, Trust Propagation, Context Drift, Scope Ambiguity Exploitation, Helpfulness Override
- **CVSS-Like Scoring** — every finding gets a 0.0–10.0 severity score + critical/high/medium/low tier
- **CI/CD Integration** — exits with code `1` on critical/high findings, making it a drop-in gate in your deployment pipeline
- **Dual Output** — terminal summary + `--output report.md` for humans + `--json findings.json` for SIEM tooling

---

## Example Usage

```bash
git clone https://github.com/fajarsajid/agent-redteam
cd agent-redteam
pip install requests
export ANTHROPIC_API_KEY=sk-ant-...

# Quick security scan of your agent's system prompt
python redteam.py --prompt path/to/your/system_prompt.txt

# Full run with JSON + Markdown output
python redteam.py --prompt system_prompt.txt \
    --probes 24 --json results/findings.json --output results/report.md

# CI pipeline gate (exits 1 on critical/high)
python redteam.py --prompt system_prompt.txt --quiet

# List all attack categories
python redteam.py --list-categories
```

---

## Research Background

Built from research conducted at Purdue University evaluating safety constraint violations in LLM-based agents under adversarial prompting. Key findings from 384 trials:

| Finding | Result |
|---|---|
| Mean violation rate | **49.5%** (SD=12.1%) |
| Indirect vs. direct injection | **70.8% vs. 54.2%** |
| Single-turn vs. 7-turn violation rate | **45.8% vs. 77.1%** |
| No-tool vs. full tool access | **34.4% vs. 71.9%** |
| Most common failure mode | **Instruction Override** (28.4%) |

**Core conclusion:** Prompt-level safety constraints are insufficient for agentic deployments. Static, single-turn evaluation underestimates real-world vulnerability by ~1.7× at 7 turns.

---

## Why It Fits the GitAgent Protocol

`agent-redteam` is a well-scoped, Claude-native agent with:
- A clear, singular purpose (AI security red-teaming)
- A defined behavioral contract (JSON-only output, grounded analysis, no hallucinated features)
- Explicit tool skills (probe generation, vulnerability analysis, incident reporting)
- CI-compatible exit codes and structured output for pipeline integration

*Part of the [Open GAP Registry](https://registry.gitagent.sh) — the catalog of portable AI agents.*
