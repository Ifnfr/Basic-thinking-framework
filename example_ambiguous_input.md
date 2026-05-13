# EXAMPLE — Ambiguous Input Processing

This example shows how the framework handles a request that could be interpreted multiple ways, using the **interpretive uncertainty** protocol from `UNCERTAINTY_HANDLING.md`.

---

## Input (User Query)

```
"How do I make my app faster?"
```

---

## Framework Processing (Internal — not shown to user)

### PHASE 1 — Input Parsing

```
PRIMARY INTENT:
  Improve performance of the user's "app" — direction unclear

SECONDARY INTENTS:
  - Likely wants actionable steps, not just theory
  - Likely expects the answer to be applicable to *their* app

CONSTRAINTS IDENTIFIED:
  - None stated

AMBIGUITIES (critical):
  - What kind of app?   (web / mobile / desktop / backend service / CLI)
  - What stack?         (React / iOS / Python / …)
  - What does "faster" mean?
      → Page load time?
      → Runtime responsiveness / frame rate?
      → API latency?
      → Backend throughput?
      → Build / CI time?
  - What's the current bottleneck? (often already known by the user)

CLASSIFICATION: Ambiguous — multiple plausible interpretations,
                answer differs dramatically between them.
```

### PHASE 2 — Interpretation Decision

Apply the `UNCERTAINTY_HANDLING.md` **Type 2 — Interpretive Uncertainty** protocol:

```
1. State interpretation explicitly
2. Answer the most likely interpretation usefully
3. Acknowledge alternatives briefly
4. Invite correction without blocking the response
```

Most likely interpretation (priors, in rough order):
1. **Web app, frontend performance** (most common context for this phrasing)
2. **Backend API latency**
3. **Mobile app responsiveness**

Strategy: give a useful **cross-cutting diagnostic framework** that works regardless of stack, then invite the user to narrow it down for a specific plan.

Structure: Lead with interpretation → diagnostic-first framework → invitation to narrow down.

### PHASE 3 — Knowledge Audit

```
HIGH CONFIDENCE:
  - General performance methodology: measure first, then optimize
  - Common bottleneck categories (network, rendering, compute, I/O)
  - The "premature optimization" trap is real and common

MODERATE CONFIDENCE:
  - Typical hot spots per stack (varies by version and workload)

UNKNOWN:
  - The user's actual stack, scale, and current bottleneck
```

---

## Output (What the user sees)

---

**Quick check on what you mean by "faster" — I'll assume it's a web app and you're worried about page load or runtime responsiveness. If it's a mobile app, a backend API, or something else, let me know and I'll adjust.**

Before touching code, the most useful move is almost always the same: **measure first, optimize second.** Performance problems feel obvious but rarely are — the bottleneck you assume usually isn't the real one.

### A 3-step diagnostic framework

**1. Pick the right metric for "faster"**

Different metrics need different fixes. Clarify which of these you care about:

| Metric | Typical concern | What to look at |
|---|---|---|
| Initial load time | "First view feels slow" | Bundle size, network waterfall, server response time |
| Interaction latency | "Clicks feel laggy" | Main-thread work, re-renders, input handlers |
| Smoothness | "Scroll/animation stutters" | Frame rate, layout thrashing, long tasks |
| API response time | "Backend feels slow" | Query time, N+1 patterns, serialization cost |
| Build / dev loop time | "Iteration is slow" | Build tool config, cache hit rates |

**2. Profile before changing anything**

Use the right tool for the metric you picked:

- **Browser runtime:** the browser's built-in performance / profiler panel
- **Backend latency:** request tracing, database query logs, an APM tool
- **Bundle size:** your bundler's analyzer output
- **Mobile:** the platform's profiler (Instruments on iOS, Android Studio Profiler on Android)

The goal is to find the **single biggest contributor** to the metric you care about. Optimize that first.

**3. Apply the smallest change that moves the needle**

Optimization follows a long-tail distribution — typically 1–3 changes account for most of the win. Resist the urge to rewrite broadly.

---

### Common wins, by category

These are starting hypotheses — verify with a profiler before committing:

- **Initial load:** code-splitting, lazy-loading routes, smaller images, HTTP caching
- **Interaction latency:** debounce/throttle heavy handlers, move work off the main thread, memoize expensive renders
- **API latency:** fix N+1 database queries, add targeted indexes, cache reads that repeat
- **Perceived speed:** skeleton screens, optimistic UI — sometimes perceived speed matters more than actual speed

---

### What I'd need to give a specific answer

- What kind of app? (web / mobile / desktop / backend)
- What's the stack? (framework, language, database)
- What's the symptom? ("X takes N seconds, should take <M")
- Have you profiled it yet? If so, what did you find?

With those four, I can point you at the specific bottleneck and fix rather than a general framework.

---

## What the Framework Achieved

| Dimension | How it was applied |
|---|---|
| **Interpreted openly** | Stated the assumption ("web app, load/runtime") in the lead so the user can correct it in one message |
| **Didn't block on clarification** | Gave a useful answer under the chosen interpretation rather than asking first and waiting |
| **Scaled to uncertainty** | Used a diagnostic framework (stack-agnostic) rather than a specific fix (stack-dependent) |
| **Invited a narrowing follow-up** | Ended with a specific list of 4 questions, not a vague "let me know if you have more questions" |
| **Calibrated confidence** | Marked common wins as "starting hypotheses — verify with a profiler" rather than as guaranteed fixes |

---

## Contrast — What a Weaker Response Would Look Like

```
✗ "Can you tell me more about your app?"
  (blocks on clarification the user didn't need to provide up front)

✗ "Here are 50 performance tips..."
  (false comprehensiveness — dumps options without guiding)

✗ "To make your app faster, you should use caching and lazy loading and..."
  (assumes a stack silently; no diagnostic step)

✗ "It depends on many factors."
  (true but useless — no framework, no path forward)
```

The framework-aligned response picks a most-likely interpretation, delivers value under it, and makes correction cheap — the user is never stuck.
