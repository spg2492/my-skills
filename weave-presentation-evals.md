# Weave Presentation Skill - Eval Criteria for Skill-Improver

## Goal

Improve the weave-presentation skill so generated slides match the visual richness and density of real Weave decks (not just brand colors/fonts, which are already fixed).

## Core Problem

The skill produces brand-correct slides but they risk looking **barebones** compared to real Weave decks, which typically have 20-30 visual elements per slide combining 3-5 visual systems.

## Test Inputs

1. "Create a 5-slide deck pitching agentic planning to a fast-fashion brand"
2. "Create a 3-slide deck showing Ask Isaac's costing agent ROI"
3. "Create a 6-slide deck for an NRF conference talk on agentic supply chains"

## Binary Eval Criteria

| # | Eval | Pass | Fail |
|---|------|------|------|
| 1 | **Visual density** | Content slides have 15+ visual elements (shapes, text blocks, icons, lines) beyond chrome | Slide has fewer than 10 elements - feels empty or sparse |
| 2 | **No bare bullet lists** | Every list is wrapped in a visual structure (cards, color-coded bars, icon rows, columns) | Any slide has a plain bullet list on a white background with no surrounding visual treatment |
| 3 | **Layout variety** | No two consecutive content slides use the same visual structure | Two adjacent slides both use the same pattern (e.g., two card grids in a row) |
| 4 | **Multi-system composition** | Each content slide combines 2+ visual systems (e.g., diagram + cards, stat callouts + color bars, flow + badges) | A slide uses only one visual system (e.g., just cards, or just text blocks) |
| 5 | **Purple depth** | At least 3 different purple shades are used across the deck to create hierarchy | Only 1-2 purple values used throughout |
| 6 | **Professional polish** | Slides feel like they belong alongside the real Weave intro deck - similar density and sophistication | Slides feel noticeably simpler or more "template-y" than real Weave decks |

## Reference Slides (for comparative scoring of eval 6)

- `Knowledge/weave/presentations/weave-intro-deck/images/Slide2.JPG` through `Slide6.JPG`
- These slides have 20-30 elements each, combining diagrams, icons, cards, connector lines, circular callouts, color blocks, and text hierarchy

## What Makes Real Weave Slides Rich

- Layered information density (diagrams + text + icons + supporting data)
- Grid-based card layouts with color-coded header bars
- Circular/rounded badge elements breaking up rectangular grids
- Connector lines and arrows showing relationships
- Repeating modular patterns (card grids, icon rows)
- 3+ purple shades creating visual hierarchy
- Every list wrapped in a visual structure (never naked bullets)

## Skill-Improver Settings (suggested)

- **Target skill:** `core/skills/weave-presentation/SKILL.md`
- **Runs per experiment:** 3 (PPTX generation is expensive)
- **Run interval:** 5 minutes (each run involves LLM + node + libreoffice + LLM scoring)
- **Budget cap:** 10 experiments (to start)
