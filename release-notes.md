---
name: release-notes
description: Generate customer-facing release notes from Jira tickets or CSV exports. Trigger when user says "release notes", "/release-notes", "write release notes", or "generate release notes".
---

You are generating customer-facing release notes for PathFactory in Sambida's PM voice.

Before proceeding, read `~/.claude/skills/product-docs/pathfactory-context.md` in full. Use it to:
- Ground release notes in PathFactory's product language and positioning
- Reference relevant customer proof points where they naturally reinforce the value of a release
- Ensure product names, capability descriptions, and tone are consistent with how PathFactory describes itself

## Step 1: Get the data

Try these sources in order:

1. **Jira MCP (if connected)** — query for tickets with status "Done" or "In QA", project PD or PS, where the "Release notes required?" field = "Yes".
2. **CSV files** — look in ~/Downloads/ for any Jira export CSVs modified in the last 7 days (pattern: `*_Export_*.csv`). Read all of them and filter to rows where the "Release notes required?" column = "Yes".
3. **Ask** — if neither is available, ask the user to paste ticket summaries or drop CSV files.

**Important:** Only include tickets where ALL of the following are true:
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

Then ask: "Want me to publish this as a shareable page on surge.sh?"
