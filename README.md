# AI Processing Framework

A structured framework for AI systems to process information carefully and produce comprehensive, high-quality outputs.

---

## Overview

This framework provides a systematic approach for AI models to:

- **Intake** and validate information rigorously
- **Reason** through problems with structured thinking
- **Generate** outputs that are comprehensive, accurate, and well-organized
- **Self-evaluate** before delivering results

It is model-agnostic. You can use it with any LLM that accepts a system prompt.

---

## Repository Structure

The repository is flat — all files live at the root.

```
Basic-thinking-framework/
├── README.md                        ← You are here
├── LICENSE
│
├── Core
│   ├── SYSTEM_PROMPT.md             ← Master system prompt (copy/paste ready)
│   ├── THINKING_PROTOCOL.md         ← T-R-A-C-E reasoning protocol
│   └── OUTPUT_STANDARDS.md          ← Five dimensions of output quality
│
├── Modules
│   ├── UNCERTAINTY_HANDLING.md      ← Handling gaps, ambiguity, outdated info
│   └── SELF_EVALUATION.md           ← Pre-delivery checklist
│
├── Templates
│   ├── GENERAL_RESPONSE.md          ← General-purpose response shape
│   ├── ANALYTICAL_REPORT.md         ← For deep analysis tasks
│   ├── PROBLEM_SOLVING.md           ← For debugging / troubleshooting
│   └── RESEARCH_SYNTHESIS.md        ← For research & summarization
│
└── Examples
    ├── example_complex_query.md
    └── example_ambiguous_input.md
```

> The "Core / Modules / Templates / Examples" groupings above are **logical**, not directory-based. All files are at the repo root.

---

## Quick Start

### Option 1 — Direct use as a system prompt

Copy the contents of [`SYSTEM_PROMPT.md`](./SYSTEM_PROMPT.md) into your model's system prompt field. That's it.

### Option 2 — Custom composition

1. Start from [`SYSTEM_PROMPT.md`](./SYSTEM_PROMPT.md) as the base.
2. Append the modules that match your use case (e.g. [`UNCERTAINTY_HANDLING.md`](./UNCERTAINTY_HANDLING.md) for research-heavy workflows).
3. Append a template (e.g. [`ANALYTICAL_REPORT.md`](./ANALYTICAL_REPORT.md)) if you want responses to follow a specific shape.

### Option 3 — API integration

The snippet below is **illustrative**. Replace the model identifier and client library with whatever provider you use. Paths below assume you run the script from the repository root.

```python
from pathlib import Path

# Adjust the model name to a valid model you have access to.
MODEL_NAME = "your-model-id-here"

system_prompt = Path("SYSTEM_PROMPT.md").read_text(encoding="utf-8")

# Example with the Anthropic SDK (replace with your provider's client):
# import anthropic
# client = anthropic.Anthropic()
# response = client.messages.create(
#     model=MODEL_NAME,
#     max_tokens=8192,
#     system=system_prompt,
#     messages=[{"role": "user", "content": user_query}],
# )
```

---

## Core Principles

| Principle | Description |
|-----------|-------------|
| **Precision** | Parse every piece of input before responding |
| **Transparency** | Show reasoning, not just conclusions |
| **Completeness** | Address all aspects of the request |
| **Calibration** | Express appropriate confidence levels |
| **Structured Output** | Organize information for maximum clarity |

---

## How the Pieces Fit Together

1. [`SYSTEM_PROMPT.md`](./SYSTEM_PROMPT.md) installs the baseline behavior (four phases: Parse, Reason, Construct, Evaluate).
2. [`THINKING_PROTOCOL.md`](./THINKING_PROTOCOL.md) is the internal reasoning pipeline (T-R-A-C-E) that runs inside Phase 2.
3. [`OUTPUT_STANDARDS.md`](./OUTPUT_STANDARDS.md) defines the five quality dimensions used in Phase 3.
4. [`SELF_EVALUATION.md`](./SELF_EVALUATION.md) is the canonical pre-delivery checklist used in Phase 4.
5. [`UNCERTAINTY_HANDLING.md`](./UNCERTAINTY_HANDLING.md) is pulled in whenever a response touches unknowns, ambiguity, or outdated information.
6. The four **templates** shape the final output format for common response types.

---

## License

[MIT License](./LICENSE) — free to use, modify, and distribute.
