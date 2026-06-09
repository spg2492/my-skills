---
name: product-docs
description: Generate customer-facing knowledge base documentation for PathFactory major feature releases. Trigger when user says "product docs", "/product-docs", "write product documentation", or "generate product doc".
---

You are generating a customer-facing knowledge base article for PathFactory in Sambida's voice: confident, practical, outcome-focused, educational, consultative, and professional.

This document serves both customers self-serving in a help center (published on WordPress) and internal CS/Solutions teams. Write polished, publication-ready prose throughout. Do not use bullet points or lists except where a numbered sequence is essential in "How to Use It".

Before proceeding, read the following sub-files in full:
- `pathfactory-context.md` — company background, products, proof points, and competitive positioning
- `article-template.md` — the 9-section article structure and writing instructions
- `screenshot-workflow.md` — how to capture screenshots of the primary customer workflow

---

## Step 1: Confirm release type

Ask: "Is this a major release? (Yes / No)"

- **Yes** → proceed
- **No** → stop. Let the user know this skill is designed for major releases only and suggest documenting it directly in Jira or Confluence.

---

## Step 2: Gather all available context

Without waiting for the user to volunteer information, proactively gather context from every available source. Work through the following automatically:

**Jira** — If a Jira epic key is provided or can be inferred, pull the epic and all linked stories via Jira MCP immediately. Extract user stories, acceptance criteria, feature descriptions, dependencies, known limitations, and release details.

**Confluence** — If a Confluence URL is provided, retrieve the full page content via the Atlassian MCP. Follow any linked pages that are relevant to the feature.

**Linked documents** — If the user provides file paths or pastes content from PRDs, Google Docs, Word documents, meeting notes, strategy documents, or customer feedback, read all of them in full.

**Transcripts** — If Gong or Zoom transcripts are provided as text or file paths, read them in full. Extract product decisions, customer language, use case discussions, and any framing that reflects how the team talks about the feature.

**Figma** — If a Figma link or exported assets are provided, use them to understand the interface, workflow steps, and UI labels.

After automatically gathering what is available, ask: "Is there anything else you'd like me to reference — additional documents, transcripts, or links?" Then proceed once confirmed.

---

## Step 3: Determine feature behavior and primary workflow

Before writing, reason through the following based on all gathered materials:

- What is the primary workflow a customer will follow to use this feature? Identify the start point, key steps, and end state.
- What does the feature do automatically versus what requires customer action?
- What are the key interface areas involved?
- What triggers or conditions affect how the feature behaves?
- Are there variations in behavior based on permissions, configuration, or account type?

Document your understanding of the primary workflow internally before moving to screenshots and writing.

---

## Step 4: Capture screenshots

Follow the instructions in `screenshot-workflow.md` to capture screenshots of the primary customer workflow.

---

## Step 5: Synthesize all inputs

Treat all gathered materials as equally valuable. Synthesize across everything to build a complete picture:

- Feature name, summary, and purpose
- The customer problem being solved and the intended outcome
- Which PathFactory product this belongs to
- How the feature works conceptually and what customers can expect
- The primary workflow, step by step, with interface references
- Customer scenarios, workflows, and use cases drawn from any source
- Dependencies, permissions, prerequisites, and configuration requirements
- Known limitations, edge cases, default behaviors, and constraints
- Release status and availability details
- Any specific language, framing, or positioning that should be preserved

Where sources conflict, prioritize the most customer-relevant and outcome-focused framing. Where sources complement each other, combine them into a cohesive narrative.

---

## Step 6: Write the article

Follow the structure and writing instructions in `article-template.md` exactly.

---

## Step 7: Output

Present the full article in the chat, formatted and ready to copy into WordPress. Where screenshots were captured, list them at the end with their file paths and the step they correspond to.

Then ask: "Would you like me to adjust the tone, expand any section, or add more use cases?"

---

## Step 8: Generate Word document

After the article is finalised, generate a Word document automatically:

1. Create a folder for the feature at `~/pm-playground/product-docs/[feature-slug]/` using `mkdir -p`. All files for this feature — HTML, Word document, and screenshots — live inside this folder.

2. Write the full article as an HTML file to `~/pm-playground/product-docs/[feature-slug]/[feature-slug].html`, using clean inline styles (Arial font, appropriate heading sizes, paragraph spacing). Where screenshots were captured, insert `<img src="[screenshot-path]">` tags after each corresponding numbered step in "How to Use It".

3. Run the Python script at `~/.claude/skills/product-docs/inject-images.py` to:
   - Read the HTML and convert it to a base `.docx` using `textutil -convert docx`
   - Open the `.docx` as a zip, locate the "How to Use It" steps in `word/document.xml`
   - Inject a `<w:drawing>` image paragraph after each numbered step using the corresponding screenshot file
   - Add the image files to `word/media/` and register their relationships in `word/_rels/document.xml.rels`
   - Write the final file to `~/pm-playground/product-docs/[feature-slug]/[feature-slug].docx`

4. Open the final `.docx` automatically so the user can review it.

If screenshots were not captured, skip the image injection and generate the `.docx` from the HTML as-is (textutil only).

The inject-images script template lives at `~/.claude/skills/product-docs/inject-images.py`. When running it for a new feature, update `DOCX_IN`, `DOCX_OUT`, `SCREENSHOTS_DIR`, and the `STEP_IMAGES` dict (mapping each step number that has a screenshot to its filename — omit steps with no screenshot) before executing.
