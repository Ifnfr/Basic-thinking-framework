# TEMPLATE — General Response

Default response shape for requests that don't clearly map to analysis, problem-solving, or research synthesis. Use this for explanations, conversational questions, short how-tos, and general information requests.

**Trigger conditions:** "what is", "explain", "tell me about", "how does X work", or any request without a more specific template match.

---

## Template

```markdown
## [Optional — topic heading, omit for short replies]

[**Lead — 1–3 sentences.** The direct answer. A reader who stops here
should already have the core information.]

### [Body heading — only if the response is long enough to need sections]

[Expand on the lead. Add reasoning, context, examples, or supporting
detail. One idea per paragraph. Use bullets or tables only when they
genuinely help.]

### [Optional — Caveats / When this doesn't apply]

- [Exception or edge case]
- [Scope limitation]

---

*[Optional one-line close — offer to go deeper, or point to the next
natural question. Skip for short replies.]*
```

---

## Variants by Request Size

### Short reply (≤ ~100 words)
No headings. No closing line. Just:

```markdown
[Direct answer in one paragraph. Add a second paragraph only if a
caveat or short example genuinely helps.]
```

### Medium reply (~100–400 words)
Lead paragraph + 1–2 body paragraphs + optional single caveat line. Headings usually unnecessary.

### Long reply (> ~400 words)
Use the full template above with headings. Consider switching to `ANALYTICAL_REPORT.md` or `PROBLEM_SOLVING.md` if the content fits those shapes better.

---

## Usage Notes

- **Lead first, always.** If you catch yourself writing background before the answer, reorder.
- **Match length to the question.** A one-line question rarely deserves a page of prose.
- **Skip headings for short replies** — a heading above two sentences is decorative noise.
- **The closing line is optional.** Use it only when you can offer something genuinely useful (a deeper topic, a next step, a clarification).

## What to Avoid

```
✗ "Great question! Let me explain..." — delete openers with zero content
✗ Restating the user's question before answering
✗ Adding a "Conclusion" section that just repeats the lead
✗ Using headings, bullets, and tables in a reply that's three sentences long
✗ Closing with a generic "Let me know if you have any other questions!"
```
