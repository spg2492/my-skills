# sprint-notes

Generates customer-facing release notes from Jira tickets in Sambida's PM voice. Publishes to a local markdown file and Confluence automatically.

## Trigger

Say `sprint notes`, `/sprint-notes`, `write release notes`, `generate release notes`, or `create release notes`.

## Inputs

- **Sprint name/number** (optional — auto-detects the next sprint from state file if not specified)
- Jira MCP connection (preferred) or a Jira CSV export in `~/Downloads/`

## What it does

1. Determines the target sprint (from your message, state file, or by asking)
2. Pulls tickets via Jira MCP or CSV where: Sprint = target, "Release notes required?" = Yes, Reporter = Sambida Pradhan
3. Writes release notes in plain language — customer-problem-first, no jargon
4. Saves the sprint state to `release-notes-sprint-state.md` so the next run auto-increments
5. Saves the markdown file to `~/pm-playground/release-notes/release-notes-[sprint-slug].md`
6. Creates a Confluence page in the PRG space under the release notes parent
7. Offers to publish to surge.sh for a public link

## Output format

Each feature gets:
- A plain-language headline that leads with the benefit
- 1 paragraph overview (problem + what changed)
- Sub-feature bullets with what it does + why it matters
- Status (Coming Soon / Available Now) and audience

## Supporting files

| File | Purpose |
|------|---------|
| `release-notes-sprint-state.md` | Tracks the last sprint processed for auto-increment |
