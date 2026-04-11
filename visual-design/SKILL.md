# Visual Design Router Skill — Overview

The **visual-design** skill is a dispatch layer that routes creative requests to specialized sub-skills based on project type.

## Key Sub-Skills

| Purpose | Sub-Skill |
|---------|-----------|
| Standalone visual art (.png/.pdf) | canvas-design |
| Interactive browser charts/graphs | d3js-visualization |
| Production UIs & components | frontend-design |
| HTML presentation decks | frontend-slides |
| Article diagrams & hero images | image-generator |
| AI-generated visuals | nano-banana-pro |
| Sales decks & landing pages | create-a-sales-asset |
| TikTok marketing automation | slideshow-creator |
| iOS/macOS design reference | apple-ux-guidelines |

## Routing Strategy

**Clear signals** map directly—"build a chart" → d3js, "create a poster" → canvas-design, "design a UI" → frontend-design.

**Ambiguous requests** warrant clarification: "Is this a static design artifact, interactive dashboard, working interface, or presentation?"

## Execution Pattern

1. Identify the matching sub-skill from context
2. Read that skill's full `SKILL.md` documentation
3. Follow its instructions precisely without blending approaches

The skill emphasizes "live prototype loops" for iterative visual work—using browser evaluation to test changes before committing final code.
