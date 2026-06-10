# visual-design

A routing skill that dispatches creative requests to the right specialized sub-skill based on what you're building.

## Trigger

Any visual or design request: "create a chart", "design a UI", "make a poster", "build a presentation", "generate an image".

## Sub-skills

| What you want | Sub-skill routed to |
|---|---|
| Standalone visual art (.png / .pdf) | `canvas-design` |
| Interactive browser charts / graphs | `d3js-visualization` |
| Production UIs & components | `frontend-design` |
| HTML presentation decks | `frontend-slides` |
| Article diagrams & hero images | `image-generator` |
| AI-generated visuals | `nano-banana-pro` |
| Sales decks & landing pages | `create-a-sales-asset` |
| TikTok marketing automation | `slideshow-creator` |
| iOS / macOS design reference | `apple-ux-guidelines` |

## How it routes

Clear signals map directly — "build a chart" → d3js, "create a poster" → canvas-design, "design a UI" → frontend-design.

Ambiguous requests will prompt: *"Is this a static design artifact, interactive dashboard, working interface, or presentation?"*

Once routed, the sub-skill's full `SKILL.md` is read and followed precisely.
