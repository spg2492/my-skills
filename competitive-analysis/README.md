# competitive-analysis

Produces a rigorous 7-section deep competitive analysis report for any set of companies or products. Designed for PM and product leadership — technically accurate, strategically sharp, and defensible under scrutiny.

## Trigger

Say `competitive analysis: [A] vs [B]`, `comp analysis [companies]`, `analyze competitors: X, Y, Z`, `full competitive deep-dive on [A] vs [B]`, or describe any architectural/strategic comparison request.

## Inputs

- **Company / product names** — 2 or more (be specific: "PathFactory ChatFactory vs Qualified PiperX")
- **Seed URLs** *(optional)* — product pages, architecture docs, release notes. Treated as source of truth for internal architecture. Without these, analysis relies on public research only.

## What it does

1. Runs two research tracks in parallel: ingesting provided URLs + live web research (last 6 months)
2. Produces a structured Markdown report with:
   - **Executive Summary** — core takeaway, where each product wins, biggest risk, recommendation
   - **Section 1** — Strategic Overview & Archetype (value prop, ICP, anti-ICP, recent moves)
   - **Section 2** — Architectural Blueprint & AI Governance (3-layer teardown with evidence tags)
   - **Section 3** — Execution Layer (step-by-step buyer session walkthrough)
   - **Section 4** — Feature Matrix (all companies as columns)
   - **Section 5** — Switching Costs & Integration Tax
   - **Section 6** — Roadmap Threat & PM Recommendation (Build / Partner / Ignore)
   - **Section 7** — Citations Appendix

## Evidence standards

Every claim is tagged: `[Verified]` (cited source), `[Inferred]` (deduced from behavior), or `[Strategic Interpretation]` (PM judgment). Internal implementation details are never stated as fact without documentation.
