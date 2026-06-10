# product-docs

Generates customer-facing knowledge base articles for PathFactory major feature releases, written in Sambida's voice and formatted for publication on WordPress.

## Trigger

Say `product docs`, `/product-docs`, `write product documentation`, or `generate product doc`.

## Inputs

- Jira epic key (auto-pulled via MCP if provided)
- Confluence URL (auto-pulled via MCP if provided)
- PRDs, Google Docs, meeting notes, or transcripts (paste or file path)
- Figma links or exported assets

## What it does

1. Confirms the release is a major release (stops if not)
2. Pulls all available context from Jira, Confluence, and any linked documents
3. Captures screenshots of the primary customer workflow in the browser
4. Writes a polished 9-section KB article following the template in `article-template.md`
5. Outputs the article in chat, ready to copy into WordPress
6. Generates a Word `.docx` file with embedded screenshots, saved to `~/pm-playground/product-docs/[feature-slug]/`

## Supporting files

| File | Purpose |
|------|---------|
| `article-template.md` | 9-section article structure and writing rules |
| `pathfactory-context.md` | Company background, products, proof points, and positioning |
| `screenshot-workflow.md` | How to capture screenshots of the primary workflow |
| `inject-images.py` | Python script that injects screenshots into the Word doc |
