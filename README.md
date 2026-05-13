# 🧠 AI Processing Framework

> A structured framework for AI systems to process information carefully and produce comprehensive, high-quality outputs.

---

## 📋 Overview

This framework provides a systematic approach for AI models to:
- **Intake** and validate information rigorously
- **Reason** through problems with structured thinking
- **Generate** outputs that are comprehensive, accurate, and well-organized
- **Self-evaluate** before delivering results

---

## 📁 Repository Structure

```
ai-processing-framework/
│
├── README.md                        ← You are here
│
├── core/
│   ├── SYSTEM_PROMPT.md             ← Master system prompt template
│   ├── THINKING_PROTOCOL.md         ← Step-by-step reasoning protocol
│   └── OUTPUT_STANDARDS.md          ← Output quality standards
│
├── modules/
│   ├── INPUT_ANALYSIS.md            ← Input parsing & validation rules
│   ├── KNOWLEDGE_SYNTHESIS.md       ← Knowledge integration guidelines
│   ├── UNCERTAINTY_HANDLING.md      ← How to handle gaps & ambiguity
│   └── SELF_EVALUATION.md           ← Pre-output quality checklist
│
├── templates/
│   ├── GENERAL_RESPONSE.md          ← General purpose response template
│   ├── ANALYTICAL_REPORT.md         ← For deep analysis tasks
│   ├── PROBLEM_SOLVING.md           ← For debugging / problem solving
│   └── RESEARCH_SYNTHESIS.md        ← For research & summarization
│
└── examples/
    ├── example_complex_query.md
    └── example_ambiguous_input.md
```

---

## 🚀 Quick Start

### For Direct Use (System Prompt)
Copy the contents of [`core/SYSTEM_PROMPT.md`](core/SYSTEM_PROMPT.md) into your AI system prompt.

### For Custom Integration
1. Select relevant **modules** based on your use case
2. Pick a **template** that matches your output format
3. Combine them into a single system prompt

### For API Integration
```python
import anthropic

with open("core/SYSTEM_PROMPT.md", "r") as f:
    system_prompt = f.read()

client = anthropic.Anthropic()
response = client.messages.create(
    model="claude-sonnet-4-20250514",
    max_tokens=8192,
    system=system_prompt,
    messages=[{"role": "user", "content": your_query}]
)
```

---

## 🧩 Core Principles

| Principle | Description |
|-----------|-------------|
| **Precision** | Parse every piece of input before responding |
| **Transparency** | Show reasoning, not just conclusions |
| **Completeness** | Address all aspects of the request |
| **Calibration** | Express appropriate confidence levels |
| **Structured Output** | Organize information for maximum clarity |

---

## 📄 License

MIT License — free to use, modify, and distribute.
