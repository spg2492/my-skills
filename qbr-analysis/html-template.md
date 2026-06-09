# HTML Template Spec — QBR Analysis Output

The output file must be a single self-contained HTML file. All styles must be in a `<style>` block in the `<head>`. No external CSS dependencies. No inline styles — use CSS classes throughout.

---

## Color Palette

| Element | Color |
|---|---|
| Header background | `#0d2d5e` |
| Header text | `#ffffff` |
| Where You're Seeing Value cards | `#1a7a4a` (background `#f0faf4`) |
| Growth Opportunities cards | `#b45309` (background `#fff7ed`) |
| Recommended Actions cards | `#1e40af` (background `#eff6ff`) |
| Strategic Takeaway block | `#0d2d5e` (background `#e8eef7`) |
| KPI delta positive | `#16a34a` |
| KPI delta negative | `#dc2626` |
| KPI delta neutral | `#6b7280` |
| Table header background | `#f1f5f9` |
| Table border | `#e2e8f0` |
| Page background | `#f8fafc` |
| Body text | `#1e293b` |
| Sticky bar background | `#0d2d5e` |
| Modern experience tile | background `#f0fdf4`, border `#86efac` |
| Classic experience tile | background `#fff5f5`, border `#fca5a5` |
| Always-on / RI tile | background `#f0f9ff`, border `#7dd3fc` |

---

## Typography

- Font family: `system-ui, -apple-system, sans-serif`
- Body size: `15px`
- Line height: `1.6`
- Section title: `18px`, bold, `#0d2d5e`
- Table: `14px`
- Insight block body: `14px`, line-height `1.65`

---

## CSS Architecture

All styles go in a single `<style>` block in `<head>`. Do not use inline styles. Use the class system below consistently.

```css
*, *::before, *::after { box-sizing: border-box; }
body { margin: 0; font-family: system-ui, -apple-system, sans-serif; font-size: 15px; line-height: 1.6; background: #f8fafc; color: #1e293b; }
.container { max-width: 960px; margin: 0 auto; padding: 24px; }

/* Section titles — numbered circle badge */
h2.section-title { font-size: 18px; font-weight: 700; color: #0d2d5e; margin: 40px 0 4px; display: flex; align-items: center; gap: 10px; }
h2.section-title .num { background: #0d2d5e; color: #fff; border-radius: 50%; width: 26px; height: 26px; display: inline-flex; align-items: center; justify-content: center; font-size: 13px; flex-shrink: 0; }
.section-rule { border: none; border-top: 2px solid #e2e8f0; margin: 8px 0 20px; }

/* Insight blocks — split "What it shows / Key takeaway" layout */
.insight { background: #fff; border: 1px solid #e2e8f0; border-radius: 10px; padding: 16px 20px; margin: 0 0 20px; }
.insight-row { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
@media (max-width: 640px) { .insight-row { grid-template-columns: 1fr; } }
.insight-label { font-size: 11px; font-weight: 700; text-transform: uppercase; letter-spacing: 0.07em; margin-bottom: 4px; }
.insight-label.shows { color: #6b7280; }
.insight-label.takeaway { color: #0d2d5e; }
.insight p { margin: 0; font-size: 14px; line-height: 1.65; color: #334155; }
.insight p strong { color: #0d2d5e; }

/* Pills — use for content type badges */
.pill { display: inline-block; padding: 2px 8px; border-radius: 12px; font-size: 12px; font-weight: 500; white-space: nowrap; }
.pill-blue  { background: #e0e7ff; color: #3730a3; }
.pill-green { background: #dcfce7; color: #166534; }
.pill-amber { background: #fef3c7; color: #92400e; }
.pill-gray  { background: #f1f5f9; color: #475569; }
.pill-red   { background: #fee2e2; color: #991b1b; }
.pill-teal  { background: #ccfbf1; color: #0f766e; }

/* Deltas */
.delta-pos { color: #16a34a; font-weight: 600; }
.delta-neg { color: #dc2626; font-weight: 600; }
.delta-neutral { color: #6b7280; }

/* Stat chips — compact metric display (used inside cards, insight blocks) */
.stat-chip { display: inline-flex; flex-direction: column; background: rgba(255,255,255,0.7); border: 1px solid rgba(0,0,0,0.08); border-radius: 8px; padding: 6px 12px; margin: 4px 4px 0 0; min-width: 80px; }
.stat-chip .chip-val { font-size: 17px; font-weight: 700; line-height: 1.2; }
.stat-chip .chip-lbl { font-size: 11px; color: #6b7280; text-transform: uppercase; letter-spacing: 0.04em; }

/* Card grid — 2-column layout for narrative cards */
.card-grid-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin-bottom: 12px; }
.card-grid-2 .card-full { grid-column: 1 / -1; }
@media (max-width: 640px) { .card-grid-2 { grid-template-columns: 1fr; } }

/* Narrative cards */
.card-green  { background: #f0faf4; border-left: 4px solid #1a7a4a; border-radius: 8px; padding: 20px; box-shadow: 0 1px 3px rgba(0,0,0,0.04); }
.card-orange { background: #fff7ed; border-left: 4px solid #b45309; border-radius: 8px; padding: 20px; box-shadow: 0 1px 3px rgba(0,0,0,0.04); }
.card-blue   { background: #eff6ff; border-left: 4px solid #1e40af; border-radius: 8px; padding: 20px; box-shadow: 0 1px 3px rgba(0,0,0,0.04); }
.card-green h3  { color: #1a7a4a; margin: 0 0 8px; font-size: 15px; }
.card-orange h3 { color: #b45309; margin: 0 0 8px; font-size: 15px; }
.card-blue h3   { color: #1e40af; margin: 0 0 8px; font-size: 15px; }
.card-green p, .card-orange p, .card-blue p { margin: 8px 0 0; font-size: 14px; line-height: 1.65; }

/* Experience tiles — modern vs classic vs always-on/RI visual distinction */
.exp-strip { display: grid; grid-template-columns: repeat(3, 1fr); gap: 12px; margin: 0 0 8px; }
@media (max-width: 640px) { .exp-strip { grid-template-columns: 1fr; } }
.exp-tile { border-radius: 8px; padding: 16px; border: 1px solid #e2e8f0; }
.exp-tile .exp-label { font-size: 11px; font-weight: 700; text-transform: uppercase; letter-spacing: 0.06em; margin-bottom: 4px; }
.exp-tile .exp-name  { font-size: 16px; font-weight: 700; margin-bottom: 12px; }
.exp-tile .exp-row   { display: flex; justify-content: space-between; font-size: 13px; margin-bottom: 4px; }
.exp-tile .exp-row .val { font-weight: 600; }
.exp-tile.classic { background: #fff5f5; border-color: #fca5a5; }
.exp-tile.modern  { background: #f0fdf4; border-color: #86efac; }
.exp-tile.always-on { background: #f0f9ff; border-color: #7dd3fc; }
.exp-tile.classic .exp-label    { color: #991b1b; }
.exp-tile.modern .exp-label     { color: #166534; }
.exp-tile.always-on .exp-label  { color: #0369a1; }

/* Insight block two-column split */
.insight-half { min-width: 0; }

/* Tables */
table { width: 100%; border-collapse: collapse; font-size: 14px; margin-top: 8px; }
th { padding: 10px 12px; text-align: left; border: 1px solid #e2e8f0; background: #f1f5f9; font-weight: 600; }
td { padding: 9px 12px; border: 1px solid #e2e8f0; vertical-align: middle; }
tr:nth-child(even) td { background: #fafbfc; }

/* Inline bar — for table cells showing proportional values */
.tbar-wrap { display: flex; align-items: center; gap: 8px; }
.tbar { height: 8px; border-radius: 4px; background: #bfdbfe; flex-shrink: 0; }
.tbar.green { background: #86efac; }

/* 2-column table grid */
.table-grid-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; }
@media (max-width: 720px) { .table-grid-2 { grid-template-columns: 1fr; } }

/* Collapsible detail sections */
details { margin-bottom: 8px; border: 1px solid #e2e8f0; border-radius: 8px; overflow: hidden; }
details summary { padding: 13px 16px; cursor: pointer; font-weight: 600; font-size: 14px; background: #f8fafc; color: #0d2d5e; display: flex; justify-content: space-between; align-items: center; list-style: none; user-select: none; }
details summary::-webkit-details-marker { display: none; }
details summary .sum-right { font-size: 12px; color: #94a3b8; font-weight: 400; display: flex; align-items: center; gap: 8px; }
details summary:hover { background: #f1f5f9; }
details .details-body { padding: 0 16px 16px; }
details[open] .toggle-arrow { transform: rotate(180deg); }
.toggle-arrow { display: inline-block; transition: transform 0.2s; }

/* Sub-heading inside data sections */
h3.sub-heading { font-size: 15px; font-weight: 700; color: #0d2d5e; margin: 28px 0 12px; }

/* Chart container */
.chart-wrap { background: #fff; border: 1px solid #e2e8f0; border-radius: 10px; padding: 20px; margin-bottom: 4px; overflow: hidden; }
.chart-wrap svg { width: 100%; display: block; }

/* Tooltip (for interactive SVG charts) */
#tt { position: fixed; background: rgba(15,23,42,0.93); color: #fff; padding: 10px 14px; border-radius: 8px; font-size: 13px; pointer-events: none; display: none; z-index: 9999; max-width: 230px; line-height: 1.55; box-shadow: 0 4px 20px rgba(0,0,0,0.28); }
#tt strong { color: #93c5fd; }
#tt .tt-row { display: flex; justify-content: space-between; gap: 16px; margin-top: 3px; }
#tt .tt-row span:last-child { font-weight: 600; }

/* Sticky mini KPI bar */
#sticky-bar { position: fixed; top: 0; left: 0; right: 0; z-index: 200; background: #0d2d5e; color: #fff; padding: 8px 24px; display: flex; align-items: center; gap: 20px; font-size: 13px; transform: translateY(-100%); transition: transform 0.25s ease; box-shadow: 0 2px 12px rgba(0,0,0,0.2); }
#sticky-bar.visible { transform: translateY(0); }
#sticky-bar .s-item { display: flex; flex-direction: column; }
#sticky-bar .s-val { font-size: 16px; font-weight: 700; line-height: 1.1; }
#sticky-bar .s-lbl { font-size: 10px; opacity: 0.7; text-transform: uppercase; letter-spacing: 0.05em; }
#sticky-bar .s-div { width: 1px; height: 32px; background: rgba(255,255,255,0.2); }
#sticky-bar .s-title { font-weight: 600; opacity: 0.8; flex: 1; }
.s-neg { color: #fca5a5; }
.s-pos { color: #86efac; }
```

---

## Page Layout

```
[Sticky KPI Bar] ← fixed, hidden until user scrolls past main KPI bar
[Header]
[Platform Maturity Callout] ← optional; include only when the mix of modern vs Classic Experience usage is a meaningful part of the story
[KPI Bar] ← id="kpi-bar", triggers sticky bar visibility
[Executive Summary]
[Where You're Seeing Value — 3 cards, 2-column grid]
[Growth Opportunities — 1–2 cards]
[Recommended Actions — 3 cards, 2-column grid]
[Strategic Takeaway]
[Chart 1: Monthly KPI Trend — SVG line chart]
[Chart 2: Topic Engagement vs. Conversion — SVG bubble/bar chart]
[Chart 3: Conversions by Content Type — SVG bar chart]
[Experience Tiles — exp-strip grid, modern vs legacy]
[Collapsible Detail Tables — <details> elements]
[Data Gaps & Notes] ← only if gaps exist
[Footer]
[Tooltip div — #tt, hidden by default]
```

Max content width: `960px`, centered, padding `24px`.

---

## Sticky KPI Bar

Appears fixed at top of viewport once user scrolls past the main KPI bar. Triggered by IntersectionObserver on `#kpi-bar`. Shows 5–6 key metrics inline.

```html
<!-- STICKY MINI KPI BAR -->
<div id="sticky-bar">
  <span class="s-title">[Customer] — [Period]</span>
  <div class="s-div"></div>
  <div class="s-item"><span class="s-val">[VALUE]</span><span class="s-lbl">Visitors</span></div>
  <div class="s-div"></div>
  <div class="s-item"><span class="s-val [s-neg|s-pos]">[VALUE]</span><span class="s-lbl">Form Rate</span></div>
  <div class="s-div"></div>
  <div class="s-item"><span class="s-val [s-neg|s-pos]">[VALUE]</span><span class="s-lbl">Form Fills</span></div>
  <div class="s-div"></div>
  <div class="s-item"><span class="s-val">[VALUE]</span><span class="s-lbl">Engagement</span></div>
  <div class="s-div"></div>
  <div class="s-item"><span class="s-val [s-neg|s-pos]">[▲/▼ YoY]</span><span class="s-lbl">Form Rate YoY</span></div>
</div>
```

JS to activate:
```javascript
const stickyBar = document.getElementById('sticky-bar');
const kpiBar    = document.getElementById('kpi-bar');
const obs = new IntersectionObserver(entries => {
  stickyBar.classList.toggle('visible', !entries[0].isIntersecting);
});
obs.observe(kpiBar);
```

---

## Header

```html
<header style="background:#0d2d5e; color:#fff; padding:32px 24px;">
  <h1 style="margin:0; font-size:28px;">[Customer Name] — Quarterly Business Review</h1>
  <p style="margin:8px 0 0; opacity:0.85;">[QBR Period] &nbsp;|&nbsp; Prepared [Date]</p>
</header>
```

---

## Platform Maturity Callout (Optional)

Include this block only when the mix of modern vs Classic Experience usage is a meaningful part of the QBR story — for example, when Classic Experiences are carrying most of the traffic, when the customer has recently adopted modern modules, or when a modernization recommendation is central to the narrative.

Use a subdued banner style that appears between the header and the KPI bar. Keep the message to one sentence — it should surface the headline signal, not explain all the evidence.

```html
<!-- PLATFORM MATURITY CALLOUT — include only when relevant -->
<div style="background:#fef9c3; border-left:4px solid #ca8a04; padding:14px 24px; font-size:14px; color:#713f12;">
  <strong>Platform note:</strong> [One-sentence framing of the maturity signal — e.g. "Most traffic this period came through Classic Experiences — see experience performance for modernization opportunities." or "Adoption of Content Playlists and Templated Experiences increased this quarter, reflecting a stronger modern campaign motion."]
</div>
```

Do not include this block if the experience mix is unremarkable or if the data does not clearly support a maturity narrative.

---

## KPI Bar

6 key metrics displayed horizontally. Add `id="kpi-bar"` so the sticky bar IntersectionObserver can watch it.

```html
<div id="kpi-bar" style="display:flex; gap:12px; flex-wrap:wrap; margin:24px 0;">
  <div style="flex:1; min-width:140px; background:#fff; border:1px solid #e2e8f0; border-radius:8px; padding:16px;">
    <div style="font-size:12px; color:#6b7280; text-transform:uppercase; letter-spacing:0.05em;">Total Visitors</div>
    <div style="font-size:24px; font-weight:700; margin:4px 0;">[VALUE]</div>
    <div class="[delta-pos|delta-neg|delta-neutral]" style="font-size:13px;">[▲/▼] [X]% YoY</div>
  </div>
  <!-- repeat for each KPI -->
</div>
```

The 6 KPIs to always include:
1. Total Visitors
2. Engagement Rate
3. Binge Rate
4. Form Capture Rate
5. Total Form Fills
6. CTA Click Rate (fall back to Total Downloads if CTA data is unavailable)

---

## Customer Goals Scorecard (Optional)

Include this block between the Executive Summary and the "Where You're Seeing Value" section when a QBR brief or customer context file was found. Omit entirely if no context files were present.

Add this CSS to the `<style>` block:

```css
/* Goals scorecard */
.goals-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 12px; margin-bottom: 8px; }
.goal-card { background: #fff; border: 1px solid #e2e8f0; border-radius: 10px; padding: 16px 18px; }
.goal-card .goal-title { font-size: 14px; font-weight: 700; color: #0d2d5e; margin: 0 0 8px; }
.goal-card .goal-evidence { font-size: 13px; color: #475569; margin: 6px 0; line-height: 1.55; }
.goal-card .goal-next { font-size: 13px; color: #0d2d5e; margin: 10px 0 0; padding-top: 8px; border-top: 1px solid #f1f5f9; }
.goal-card .goal-next strong { font-weight: 600; }
.badge { display: inline-flex; align-items: center; gap: 5px; padding: 3px 10px; border-radius: 20px; font-size: 12px; font-weight: 600; margin-bottom: 6px; }
.badge-green  { background: #dcfce7; color: #166534; }
.badge-amber  { background: #fef3c7; color: #92400e; }
.badge-gray   { background: #f1f5f9; color: #475569; }
```

HTML template:

```html
<h2 class="section-title">Customer Goals Scorecard</h2>
<hr class="section-rule">
<p style="font-size:14px; color:#475569; margin: -8px 0 16px;">Based on goals defined in [context filename(s)]. Status reflects [QBR Period] data.</p>
<div class="goals-grid">

  <!-- One card per goal — repeat this block -->
  <div class="goal-card">
    <div class="goal-title">[Goal Name]</div>
    <span class="badge [badge-green|badge-amber|badge-gray]">[✓ On Track | ⚠ In Progress | ✗ Not Yet Started]</span>
    <div class="goal-evidence">[1–2 specific data points from the parsed data that support the status assessment]</div>
    <div class="goal-next"><strong>Next step:</strong> [One actionable sentence tied to the data]</div>
  </div>

</div>
```

**Status badge rules:**
- `badge-green` + "✓ On Track" — data shows clear, positive movement directly tied to this goal
- `badge-amber` + "⚠ In Progress" — foundational work is underway or partial progress is visible, but outcome not yet achieved
- `badge-gray` + "✗ Not Yet Started" — goal is stated but no activation or meaningful data signal exists yet

**Writing rules for this section:**
- Goal titles should be short (3–6 words), plain language — not copied verbatim from the brief if the original is too long or jargon-heavy
- Evidence must come from the parsed data — never invented or inferred from context alone
- Next step must be specific and directly actionable, not generic advice
- Limit to 4–6 goal cards. If goals are very similar, combine them into one card rather than splitting

---

## Section Titles

Use numbered circle badges for all major sections:

```html
<h2 class="section-title"><span class="num">1</span> Where You're Seeing Value</h2>
<hr class="section-rule">
```

Number each section sequentially: 1 = Where You're Seeing Value, 2 = Growth Opportunities, 3 = Recommended Actions, then continue for data sections.

---

## Narrative Cards

### Where You're Seeing Value — 2-column grid
```html
<div class="card-grid-2">
  <div class="card-green">
    <h3>[Strength Title]</h3>
    <p>[Specific data point and why it matters as a business outcome]</p>
  </div>
  <div class="card-green">...</div>
  <div class="card-green card-full">...</div> <!-- spans both columns -->
</div>
```

### Growth Opportunities
```html
<div class="card-orange">
  <h3>[Opportunity Title]</h3>
  <p>[Constructively framed gap with supporting data evidence]</p>
</div>
```

### Recommended Actions — 2-column grid
```html
<div class="card-grid-2">
  <div class="card-blue">
    <h3>Action 1 — [Action Title]</h3>
    <p>[Specific actionable step tied directly to a finding]</p>
  </div>
  <!-- ... -->
</div>
```

### Strategic Takeaway
```html
<div style="background:#e8eef7; border-left:4px solid #0d2d5e; border-radius:8px; padding:24px; margin:32px 0;">
  <h2 style="color:#0d2d5e; margin:0 0 8px;">Strategic Takeaway</h2>
  <p style="margin:0; font-size:17px; font-weight:500;">[One sentence — the most important insight a CEO could repeat in a meeting]</p>
</div>
```

---

## SVG Charts

Four chart sections follow the narrative. Each uses `.chart-wrap` with an SVG element rendered by inline JavaScript. Charts must be interactive — hover tooltips using `#tt`.

```html
<h3 class="sub-heading">[Chart Title]</h3>
<div class="chart-wrap">
  <svg id="[chart-id]" viewBox="0 0 760 260"></svg>
</div>
```

Immediately after each chart, include an insight block explaining what it shows and the key takeaway.

### Required charts (in order):

1. **Monthly KPI Trend** — line chart, visitors (bars) + form capture rate (line) by month. Hover shows full metric breakdown per month.

2. **Topic Engagement vs. Conversion** — bubble chart, x=avg engagement score, y=total views, bubble size=form fills. Green fill = converting topics, red = zero conversions. Hover shows topic name, views, engagement, fills.

3. **Conversions by Content Type** — horizontal bar chart ranked by total conversions. Show views alongside conversions as a secondary bar. Hover shows content type, views, fills, conversion rate.

4. **Experience Performance by Type** — grouped bar chart comparing visitor volume and form rate across experience types and modules. Color-code by category: modern (green), Classic Experiences (amber/red), always-on / RI (blue).

All chart JS must be self-contained in a single `<script>` block at end of body.

---

## Insight Block

Used after every chart and inside collapsible detail tables. Split layout: left = "What this shows", right = "Key takeaway".

```html
<div class="insight">
  <div class="insight-row">
    <div class="insight-half">
      <div class="insight-label shows">📊 What this shows</div>
      <p>[Explanation of what the chart/table is showing and how to read it]</p>
    </div>
    <div class="insight-half">
      <div class="insight-label takeaway">💡 Key takeaway</div>
      <p>[The most important business signal from this data. Be specific — reference actual values.]</p>
    </div>
  </div>
</div>
```

---

## Experience Tiles

Visual comparison of experience types and modules, color-coded by category. Used before the collapsible tables. Only render tiles for modules where data is available.

```html
<div class="exp-strip">
  <div class="exp-tile [modern|classic|always-on]">
    <div class="exp-label">[🟢 Modern | 🟡 Classic | 🔵 Always-On / RI]</div>
    <div class="exp-name">[Experience Type or Module]</div>
    <div class="exp-row"><span>Visitors</span><span class="val">[VALUE]</span></div>
    <div class="exp-row"><span>Visitors YoY</span><span class="val [delta-pos|delta-neg]">[▲/▼ VALUE]</span></div>
    <div class="exp-row"><span>Form Capture Rate</span><span class="val">[VALUE]</span></div>
    <div class="exp-row"><span>Form Rate YoY</span><span class="val [delta-pos|delta-neg]">[▲/▼ VALUE]</span></div>
    <div class="exp-row"><span>Binge Rate</span><span class="val">[VALUE]</span></div>
    <div class="exp-row"><span>Avg Session</span><span class="val">[VALUE]</span></div>
  </div>
</div>
```

**Tile classification:**
- Content Playlists, Templated Experiences → `.modern` (🟢 Modern)
- Target, Recommend, Microsites → `.classic` (🟡 Classic)
- Website Tools, PFRI → `.always-on` (🔵 Always-On / RI)

For Website Tools tiles, show: visitors (or sessions), engagement rate, and top recommendation click-through where data is available. For PFRI tiles, show: active buyers, active accounts or opportunities, and seller shares where data is available. Omit rows where data is not present rather than showing empty values.

---

## Collapsible Detail Tables

All supporting data tables go inside `<details>` elements. Each collapses by default and includes a summary line with a key takeaway.

```html
<details>
  <summary>[Table Title] — [quick context e.g. "318 assets, 16 types"]
    <span class="sum-right">
      <em>[One-line key takeaway visible in collapsed state]</em>
      <span class="toggle-arrow">▼</span>
    </span>
  </summary>
  <div class="details-body">
    <div class="insight" style="margin-top:12px;">
      <!-- insight block here -->
    </div>
    <table>
      <thead><tr><th>[Column]</th></tr></thead>
      <tbody><tr><td>[Value]</td></tr></tbody>
    </table>
  </div>
</details>
```

### Required collapsible tables (in order):
1. Experience Performance — type, visitors, YoY, form rate, form rate YoY, binge rate, avg session
2. Top Performing Experiences — name, type (pill), visitors, form rate, download rate
3. Content Type Summary — type (pill), views, avg engagement, form fills, downloads, total conversions
4. Topic Performance — topic, views, avg engagement, form fills (only if topic data exists)
5. Industry Breakdown — industry, visitors, YoY delta
6. Monthly Performance Snapshot — month, visitors, engagement rate, binge rate, form captures
7. Pipeline & Revenue Influence — metric, value, YoY delta, notes (include form fills, CTA clicks, downloads, pipeline influenced, Closed Won attribution where available; include PFRI buyer/account/opportunity signals where PFRI data is present; omit this table entirely if no pipeline or revenue data is available)

Use inline bars (`.tbar-wrap` / `.tbar`) in table cells to show proportional values visually.

Use pill badges for content type and experience type labels:
```html
<span class="pill pill-blue">[Content Type]</span>
<span class="pill pill-green">[Modern Experience]</span>
<span class="pill pill-amber">[Legacy Experience]</span>
```

---

## Tooltip

Place at the end of `<body>`, before `</body>`. Used by SVG chart hover interactions.

```html
<div id="tt"><!-- populated by JS --></div>
```

JS helpers:
```javascript
const tt = document.getElementById('tt');
function showTT(e, html) { tt.innerHTML = html; tt.style.display = 'block'; moveTT(e); }
function moveTT(e) {
  const x = e.clientX, y = e.clientY, w = tt.offsetWidth, h = tt.offsetHeight;
  tt.style.left = (x + 16 + w > window.innerWidth ? x - w - 10 : x + 14) + 'px';
  tt.style.top  = (y + 16 + h > window.innerHeight ? y - h - 10 : y + 12) + 'px';
}
function hideTT() { tt.style.display = 'none'; }
```

---

## Data Gaps & Notes

Only render if gaps exist. Omit entirely if data was complete.

```html
<div style="background:#fafafa; border:1px solid #e2e8f0; border-radius:8px; padding:20px; margin:32px 0;">
  <h2 style="font-size:16px; color:#6b7280; margin:0 0 12px;">Data Gaps & Notes</h2>
  <ul style="margin:0; padding-left:20px; color:#6b7280; font-size:14px; line-height:1.8;">
    <li>[e.g. Benchmark data not available — benchmark comparison section omitted]</li>
    <li>[e.g. Topic tags missing on 78% of assets — topic analysis limited to tagged content only]</li>
  </ul>
</div>
```

---

## Footer

```html
<footer style="margin-top:48px; padding-top:16px; border-top:1px solid #e2e8f0; font-size:13px; color:#6b7280;">
  <p><strong>Data sources:</strong> [list Excel files used]</p>
  <p><strong>Missing data:</strong> [list any core Excel files not found and which sections were skipped, or "None"]</p>
  <p><strong>Context inputs:</strong> [list any context files used and briefly how each shaped the report — e.g. "QBR goal (qbr-brief.md): renewal framing applied to narrative emphasis. Customer context (context.md): maturity level and active use cases used to prioritize recommendations." — or "None: report produced from data and user-provided context only."]</p>
  <p>Generated by QBR Analysis skill &nbsp;|&nbsp; [Date]</p>
</footer>
```

---

## Rules

- No nav links to external pages — do not include upload.html, qbr.html, dashboard.html
- All styles in a single `<style>` block — no inline styles, no external stylesheets
- File must open correctly in any browser without a server
- All numbers in charts and tables must come from real parsed data — no placeholders
- SVG charts must be rendered by inline JavaScript using real data variables
- All tables must be inside `<details>` collapsible elements
- Every chart and table must be followed by an insight block
- Experience tiles must visually distinguish modern (green) from legacy (red) types
