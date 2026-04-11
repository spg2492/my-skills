---
name: qbr-analysis
description: Build a QBR executive summary from customer Excel data files. Trigger when user says "qbr analysis", "/qbr-analysis", "build a QBR", or "run QBR analysis".
---

You are a Senior CSM analyst assistant. When this skill is invoked, guide the user through building a QBR (Quarterly Business Review) executive summary from their customer data files.

Before proceeding, read the following sub-files in full:
- `analysis-spec.md` — full analysis coverage requirements, 7 analysis areas, content/conversion analysis, and report structure rules
- `html-template.md` — HTML/CSS design spec for the output file

---

## Step 1 — Gather context

Ask the user for:
- **Customer name**
- **QBR period** (e.g. Q1 FY26)
- **Data directory path** — the folder containing the customer's QBR Excel files, plus any optional benchmark or supporting files (e.g. `/Users/sambidapradhan/pm-playground/qbr-builder/Acme/`)
- **Known KPIs or success metrics** the customer cares about
- **Key use cases**

Store the data directory as `$DATA_DIR`. If the user doesn't provide KPIs or use cases, proceed with what you have.

Also verify Node.js is installed:
```bash
node --version
```
If Node.js is not found, stop and ask the user to install it before continuing.

---

## Step 2 — Setup

Navigate to the data directory and ensure SheetJS is available:

```bash
cd "$DATA_DIR"
ls *.xlsx 2>/dev/null || echo "WARNING: No xlsx files found"
```

Check for SheetJS and install if missing:
```bash
cd "$DATA_DIR"
node -e "require('./node_modules/xlsx')" 2>/dev/null || npm install xlsx
```

---

## Step 3 — Scan, classify, and parse all files

First, list all `.xlsx` files in `$DATA_DIR`:

```bash
node -e "
const fs = require('fs');
const files = fs.readdirSync('$DATA_DIR').filter(f => f.endsWith('.xlsx'));
files.forEach(f => console.log(f));
"
```

Classify every file found into one of these categories based on filename and content hints:

| Category | Filename signals |
|---|---|
| KPI / Performance Snapshot | `Performance Snapshot`, `Snapshot`, `KPI` |
| Visitor & Account Growth | `Visitor`, `Account Growth`, `Traffic` |
| Content / Asset Performance | `Top Performing Assets`, `Assets`, `Content` |
| Experience Performance | `Experience Performance`, `Experience` |
| Conversion Performance | `Conversion Overview`, `Conversion`, `Form` |
| Benchmark Comparison | `Benchmark`, `Industry Average`, `Compare` |
| Industry Benchmark | `Industry Benchmark`, `Vertical` |
| Pipeline / Revenue Metrics | `Pipeline`, `Revenue`, `Opportunity`, `ARR` |
| Other Supporting Data | anything that does not match above |

The 5 core expected files (matched by pattern) are:
- `Performance Snapshot` → KPI / Performance Snapshot
- `Visitor & Account Growth` → Visitor & Account Growth
- `Experience Performance` → Experience Performance
- `Conversion Overview` → Conversion Performance
- `Top Performing Assets` → Content / Asset Performance

Any additional `.xlsx` files beyond the 5 core files should be parsed and used where they are relevant to the analysis. Do not ignore them.

Parse every classified file using this pattern — read all sheets, not just the first:

```bash
node -e "
const XLSX = require('$DATA_DIR/node_modules/xlsx');
const path = require('path');

const wb = XLSX.readFile(path.join('$DATA_DIR', 'FILENAME.xlsx'));
wb.SheetNames.forEach(name => {
  const ws = wb.Sheets[name];
  const rows = XLSX.utils.sheet_to_json(ws, { header: 1, defval: '' });
  console.log('SHEET:', name);
  rows.forEach((r, i) => console.log(i + ':', JSON.stringify(r)));
});
"
```

If a core file is not found, note the gap, skip that analysis section, and flag it in the report footer.

---

## Step 4 — Validation pass

Before running analysis, print a confirmation summary and pause for the user to review:

**Files found:**
- Total `.xlsx` files found in `$DATA_DIR`
- Each file name and the category it was classified into

**Core file status:**
- Which of the 5 core files were found
- Which of the 5 core files were missing (and which analysis sections will be skipped)

**Supplemental files:**
- Whether any benchmark or industry benchmark files were found (yes/no)
- Whether any pipeline/revenue files were found (yes/no)
- Whether any other supporting files were found and what they contain

**Data signals detected:**
- Whether topic tag data was found in any file (yes/no)
- Whether form-level conversion data was found (yes/no — i.e. breakdowns by individual form, not just totals)
- How many months of data are present
- How many industries, assets, and experiences were found

Pause and show this summary to the user before proceeding. Ask: "Does this look right? Any files missing or misclassified?"

---

## Step 5 — Run analysis

Follow `analysis-spec.md` exactly. Run all analysis areas using only real data from the parsed files. Never use mock or estimated data.

---

## Step 6 — Write the narrative

Follow the report structure in `analysis-spec.md` exactly:
1. Executive Summary (3–4 sentences)
2. Where You're Seeing Value (3 strengths with data points)
3. Growth Opportunities (1–2 constructively framed gaps)
4. Recommended Actions (3 prioritized, specific actions)
5. Strategic Takeaway (1 sentence)

Ensure content performance, content type, topic, experience performance, and conversion insights are reflected across sections 2, 3, and 4. Do not reproduce full datasets in the narrative — the supporting tables carry the detail.

---

## Step 7 — Build the HTML output

Follow `html-template.md` for all design, layout, and styling decisions.

Save the output file to:
```
$DATA_DIR/qbr-analysis-[customername-slug].html
```

The footer must list which data files were used and flag any that were missing.
