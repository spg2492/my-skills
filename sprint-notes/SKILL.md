---
name: sprint-notes
description: Generate customer-facing release notes from Jira tickets or CSV exports. Trigger when user says "sprint notes", "/sprint-notes", "write release notes", "generate release notes", or "create release notes".
---

You are generating customer-facing release notes for PathFactory in Sambida's PM voice.

Before proceeding, read `~/.claude/skills/product-docs/pathfactory-context.md` in full. Use it to:
- Ground release notes in PathFactory's product language and positioning
- Reference relevant customer proof points where they naturally reinforce the value of a release
- Ensure product names, capability descriptions, and tone are consistent with how PathFactory describes itself

## Step 0: Determine the target sprint

**Important:** Always use the **Sprint** field (found in the Details tab of a Jira ticket). Never use Fix Version, Affects Version, or any other version field for filtering or grouping.

1. **Check the user's message** — if they specified a sprint (e.g., "sprint notes for Sprint 42", "sprint 15"), use that sprint as the target.
2. **Check state file** — if no sprint was specified, read `~/.claude/skills/release-notes-sprint-state.md`:
   - If the file exists and contains a sprint name → auto-target the **next** sprint. For numbered sprints (e.g., "Sprint 42"), increment by 1. For named/date-based sprints, query Jira for the sprint that follows the saved one.
   - If the file does not exist → ask the user: "Which sprint should I generate release notes for? (e.g., Sprint 42)"
3. **Confirm aloud** before proceeding — e.g., "Generating release notes for Sprint 43…"

## Step 1: Get the data

Try these sources in order:

1. **Jira MCP (if connected)** — query for tickets where the **Sprint field** (Details tab) = target sprint, status "Done" or "In QA", project PD or PS, and "Release notes required?" = "Yes". Do not filter by Fix Version or any other version field.
2. **CSV files** — look in ~/Downloads/ for any Jira export CSVs modified in the last 7 days (pattern: `*_Export_*.csv`). Read all of them and filter to rows where the **"Sprint" column** matches the target sprint AND the "Release notes required?" column = "Yes". Ignore any version/fix version columns.
3. **Ask** — if neither is available, ask the user to paste ticket summaries or drop CSV files.

**Important:** Only include tickets where ALL of the following are true:
- Sprint = target sprint
- "Release notes required?" = "Yes"
- Reporter = "Sambida Pradhan"

Skip all other tickets silently.

## Step 2: Extract what matters

From the tickets, pull:
- Summary / ticket title
- Description (especially the user story and acceptance criteria)
- Epic name (for grouping)
- Status

Ignore internal fields: story points, sprint names, assignees, technical implementation details.

## Step 3: Write the release notes

Follow this exact format and tone:

**Tone rules:**
- Write for marketers and business users, not engineers
- Lead with the customer problem being solved, not the feature name
- Use "you" language ("you can now...", "your team...")
- Keep sentences short and direct
- No jargon: no "payload", "orchestrator", "merge", "QA", "sprint"
- Each feature gets: what's new + why it matters (1-2 sentences each)

**Format:**
```
## What's New: [Feature Name]

### [Plain-language headline that leads with the benefit]

[1 paragraph overview: the problem this solves + what changed]

**[Sub-feature or step 1]**
[What it does] + [Why it matters in italics]

**[Sub-feature or step 2]**
[What it does] + [Why it matters in italics]

---
**Status:** [Coming Soon / Available Now]
**Who's it for:** [User type]
```

## Step 4: Output

Present the full release notes in the chat, ready to copy or publish.

Then do the following in order:

1. **Save sprint state** — overwrite `~/.claude/skills/release-notes-sprint-state.md` with just the sprint name/number (e.g., `Sprint 43`).

2. **Save local markdown file** — write the release notes to `~/pm-playground/release-notes/release-notes-[sprint-slug].md` (e.g., `release-notes-sprint-43.md`). Create the directory if it doesn't exist. Tell the user the file path.

3. **Publish to Confluence** — create a new page using the Atlassian MCP:
   - Tool: `mcp__claude_ai_Atlassian__createConfluencePage`
   - Cloud ID: `ab6df8ae-4b9f-4660-b2ba-96c2c38c2c86`
   - Space key: `PRG`
   - Parent page ID: `5115740165`
   - Title: `Release Notes — [Sprint Name]` (e.g., `Release Notes — Sprint 43`)
   - Content: full release notes formatted as HTML
   - Share the resulting Confluence page URL with the user so they can send it to the marketing team.

4. **Offer surge.sh** — ask: "Want me to also publish this to surge.sh for a public link?"
