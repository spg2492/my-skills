# competitive-comparison-brief

Produces a concise, scannable internal competitive comparison brief for any set of companies or products. Lighter than a full deep-dive but more substantive than a summary — designed to share with leadership or a cross-functional team.

## Trigger

Say `competitive brief on [A] vs [B]`, `comp brief for the team on [X] vs [Y]`, `internal comparison of [X] vs [Y]`, `comparison doc on [A] vs [B] for [audience]`, or any request for a concise/shareable comparison.

## Inputs

- **Company / product names** — 2 or more
- **Seed URLs** *(optional)* — treated as source of truth for product architecture
- **Intended audience** *(optional)* — adapts tone and emphasis (defaults to internal PM / cross-functional team)

## What it does

Produces a single Markdown document with:
- **Bottom Line** — 2–4 sentence core takeaway
- **Executive Summary** — 4–6 bullets covering what each product is optimized for, where each wins, strategic implication, recommendation
- **Section 1** — What these products are really competing on
- **Section 2** — Side-by-side comparison table
- **Section 3** — Capability breakdown (names major surfaces explicitly; agent operating model if applicable)
- **Section 4** — Workflow difference (how the buyer/user journey differs)
- **Section 5** — Where each wins (specific conditions, not platitudes)
- **Section 6** — Strategic implication
- **Section 7** — Recommendation / Takeaway
- **Sources**

## Evidence standards

Same rigor as the full competitive-analysis skill — `[Verified]`, `[Inferred]`, `[Strategic Interpretation]` tags. Shorter format does not mean weaker evidence.
