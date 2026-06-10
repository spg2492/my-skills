# qbr-analysis

Builds a QBR (Quarterly Business Review) executive summary from a customer's Excel data files. Produces an HTML report with narrative analysis, data tables, and strategic recommendations.

## Trigger

Say `qbr analysis`, `/qbr-analysis`, `build a QBR`, or `run QBR analysis`.

## Inputs

- **Customer name**
- **QBR period** (e.g. Q1 FY26)
- **Data directory path** — folder containing the customer's Excel files (e.g. `~/pm-playground/qbr-builder/Acme/`)

### Optional context files (place in the data directory)

| File pattern | Purpose |
|---|---|
| `*qbr*`, `*brief*`, `*goal*` | QBR goal — shapes the meeting purpose and narrative |
| `*context*`, `*profile*`, `*account*` | Customer background, maturity, use cases |
| `*quarter*`, `*notes*` | Quarterly notes and active campaigns |
| `*stakeholder*`, `*contact*` | Audience context for tone |

### Expected Excel files (core)

- Performance Snapshot
- Visitor & Account Growth
- Experience Performance
- Conversion Overview
- Top Performing Assets

## What it does

1. Scans the data directory for Excel and context files
2. Confirms the QBR goal with you before proceeding
3. Parses all Excel files using SheetJS
4. Runs 9 analysis areas per `analysis-spec.md`
5. Writes a narrative with Executive Summary, Value highlights, Growth Opportunities, and Recommended Actions
6. Saves an HTML report to `$DATA_DIR/qbr-analysis-[customer-slug].html`

## Supporting files

| File | Purpose |
|------|---------|
| `analysis-spec.md` | Full analysis spec — 9 areas, ranking logic, PathFactory module context, report structure |
| `html-template.md` | HTML/CSS design spec for the output file |
