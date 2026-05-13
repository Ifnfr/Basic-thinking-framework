# TEMPLATE — Problem Solving Response

Use this template for debugging, troubleshooting, solution design, and any request where the user has a problem that needs solving.

**Trigger conditions:** "fix", "debug", "solve", "why isn't X working", "how do I", "I'm getting an error", "help me figure out"

---

## Template

```markdown
## Problem: [One-line restatement of the problem]

### Root Cause
[State the most likely cause(s) of the problem. Be specific.
If multiple causes are possible, list them in order of likelihood.]

**Most likely cause:** [Primary cause in one sentence]

---

### Solution

[If one clear solution exists:]

**Step 1 — [Action name]**
[Instruction. Be precise. Include exact commands, values, or code.]

```[language]
[Code or command if applicable]
```

**Step 2 — [Action name]**
[Instruction]

**Step 3 — [Verify]**
[How does the user confirm the fix worked? What does success look like?]

---

### If the Solution Doesn't Work

**Alternative cause:** [Second most likely root cause]

Try:
```[language]
[Alternative fix]
```

---

### Why This Happened
[Optional but valuable — explain the underlying reason so the user
understands the problem, not just the fix. Prevents recurrence.]

---

### Related Issues to Watch For
- [Side effect or related issue that might surface next]
- [Common follow-up problem in this scenario]
```

---

## Variant: Multiple Candidate Solutions

When several approaches exist, use this structure:

```markdown
### Option A — [Name] *(Recommended)*
**When to use:** [Scenario]
**Trade-off:** [What you gain / what you give up]

[Implementation]

---

### Option B — [Name]
**When to use:** [Scenario]
**Trade-off:** [What you gain / what you give up]

[Implementation]

---

### Recommendation
Use **Option A** if [condition]. Use **Option B** if [condition].
```

---

## Usage Notes

- **Lead with the solution**, not with the diagnosis (unless the diagnosis is non-obvious and crucial)
- Always include a **verification step** — users need to know when they're done
- The "Why This Happened" section converts a fix into learning
- For code solutions: test the logic mentally before presenting it
- Be explicit about **prerequisites** before step 1

## What to Avoid

```
✗ Listing 5 possible causes without prioritizing them
✗ Providing a fix without a verification step
✗ Generic advice like "check your configuration" without specifics
✗ Showing code that hasn't been mentally verified
✗ Skipping error message analysis when one was provided
```
