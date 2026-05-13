# EXAMPLE — Complex Query Processing

This example demonstrates how the framework processes a multi-part, complex query from input to output.

---

## Input (User Query)

```
"We're building a SaaS product for small businesses. We're debating between 
a monolithic architecture and microservices. We have a team of 4 engineers 
and expect to grow to ~20 users in the first year. What should we do and why?"
```

---

## Framework Processing (Internal — not shown to user)

### PHASE 1 — Input Parsing

```
PRIMARY INTENT:
  Architecture recommendation for a SaaS product

SECONDARY INTENTS:
  - Explanation/justification for the recommendation
  - Implicit: What are the trade-offs?
  - Implicit: What are the risks of each path?

CONSTRAINTS IDENTIFIED:
  - Team size: 4 engineers (small)
  - Stage: Early (pre-launch or early launch)
  - Scale expectation: ~20 users Y1 (very low)
  - Domain: B2B SaaS

AMBIGUITIES:
  - "Small businesses" as customers — relevant for feature complexity?
  - Technology stack not specified (minor — answer is stack-agnostic)
  - Growth trajectory beyond Y1 not stated
  
CLASSIFICATION: Analytical + Recommendation
```

### PHASE 2 — Knowledge Audit

```
HIGH CONFIDENCE:
  - Monolith vs microservices trade-offs (well-established)
  - Team size as a key factor in architecture decisions
  - "Majestic Monolith" as a recognized best practice for small teams

MODERATE CONFIDENCE:
  - Specific migration paths from monolith to microservices
  - Industry norms for SaaS startups at this scale

UNCERTAINTIES:
  - Future growth trajectory (unknown)
  - Specific technical requirements of their product (unknown)
```

### PHASE 3 — Reasoning

```
Key factors in this decision:
1. Team size (4 engineers) → strongly favors simplicity
2. 20 users Y1 → no scale pressure yet
3. SaaS = evolving requirements → need flexibility
4. Microservices at this stage = massive operational overhead
   for 4 engineers (networking, deployment, service discovery, observability)
5. Industry pattern: successful SaaS companies (Shopify, Stack Overflow, 
   Basecamp) ran monoliths for years before breaking up
   
Conclusion: Monolith is strongly favored for this context.
Structure of answer: Lead with recommendation → explain why → address
microservices risks → provide migration path → caveat on future decision point
```

---

## Output (What the user sees)

---

**Go with a monolith — at least for now.** For a 4-person team targeting 20 users in year one, microservices would create far more complexity than value. Here's the full picture:

### Why Monolith Wins at Your Stage

**Team size is the deciding factor.** Microservices require significant operational infrastructure: service discovery, distributed tracing, inter-service networking, independent CI/CD pipelines, and container orchestration. Managing all of that meaningfully adds to every engineer's cognitive load — on a 4-person team, that overhead competes directly with building features.

**Your scale doesn't demand it.** 20 users generates minimal infrastructure load. The core benefit of microservices — the ability to scale individual services independently — isn't relevant until you have scale problems worth solving. Optimizing for theoretical future scale before product-market fit is a common and costly mistake.

**Speed of iteration matters more right now.** With a monolith, a developer can trace a request from HTTP handler to database query in one codebase, add a feature that spans multiple domains in a single PR, and deploy the whole thing with one pipeline. That velocity is critical in early-stage product development.

This isn't just theory — Shopify, Stack Overflow, and Basecamp ran monolithic architectures for years as large-scale products before migrating selectively. The pattern is well-established.

---

### What Makes a Good Monolith

The risk of "just build a monolith" is building an **unstructured** monolith — a big ball of mud that's genuinely hard to migrate later. Avoid this by:

- **Enforcing domain boundaries in code** — organize by feature/domain (e.g., `billing/`, `users/`, `projects/`), not by technical layer (`models/`, `controllers/`)
- **Keeping the database schema modular** — avoid cross-domain foreign keys; treat domain tables as loosely coupled from the start
- **Building clean internal APIs** — domain modules call each other through defined interfaces, not arbitrary function calls

This gives you a **"Majestic Monolith"** — a codebase that's easy to maintain now and can be decomposed into services later if and when you need to.

---

### When to Revisit This Decision

Consider moving toward microservices (or a modular "macroservices" approach) when:
- A specific domain (e.g., billing, notifications) has **meaningfully different scaling needs** from the rest
- Your team has grown to **10+ engineers** and coordination on a single repo becomes the bottleneck
- A specific service needs **independent deployment cycles** for a justified reason

At 20 users and 4 engineers, none of those conditions apply yet.

---

### One Caveat

If part of your product has a fundamentally different runtime profile — for example, a real-time event processing pipeline alongside a standard CRUD web app — a targeted separation there can make sense from day one. But that's an exception based on technical necessity, not a general architecture choice.

---

*Happy to go deeper on how to structure the monolith for clean future separation, or on specific tooling/deployment patterns for your stack.*

---

## What the Framework Achieved

| Dimension | How it was applied |
|---|---|
| **Accurate** | Claim about Shopify/Stack Overflow pattern is accurate; uncertainty about user's future trajectory acknowledged |
| **Complete** | Answered the recommendation, the reasoning, the trade-offs, and the future decision point |
| **Clear** | Lead is a direct one-sentence recommendation; no throat-clearing |
| **Structured** | Three distinct sections: recommendation rationale, implementation guidance, future trigger conditions |
| **Calibrated** | "Well-established" for industry pattern; "can make sense" (hedged) for the edge case |
