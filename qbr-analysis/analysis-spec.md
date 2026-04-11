# Analysis Spec — QBR Analysis

## PathFactory Experience Context

Use this section to interpret performance across PathFactory experience types. Not all experience types are equivalent — some are modern platform capabilities, others are legacy. This context must inform the executive summary narrative, What's Working, What to Watch, and Recommendations. Do not treat legacy and modern experiences as interchangeable.

---

### Content Playlists

**What it is:** The modern, unified PathFactory experience. Curated content journeys that adapt dynamically to visitor behavior, supporting personalization, AI-driven recommendations, and seamless multi-asset consumption in a single session.

**Strong performance indicates:** The buyer is progressing through a well-structured content journey. High binge rates and long session times signal that content sequencing is working. Form fills and CTA clicks here reflect a modern, optimized conversion path.

**Low performance may indicate:** Content sequencing is weak, assets are not relevant to the intended audience, or personalization rules are not configured effectively. Low engagement on a Playlist is an optimization problem, not a content problem.

**Guidance:** Content Playlists are the primary vehicle for personalization at scale. When they perform well, highlight the maturity of Aplan's content strategy. When they underperform relative to legacy types, flag it as a configuration and sequencing opportunity — not a reason to revert to legacy formats.

---

### Templated Experiences

**What it is:** The modern campaign framework replacing Microsites. Supports reusable, templatized campaign structures with dynamic personalization, AI-assisted templating, and AI translation capabilities. Designed for ABM, event, and industry-specific campaigns at scale.

**Strong performance indicates:** Campaign targeting and personalization are working. High form rates or binge rates on Templated Experiences — even at low visitor volumes — reflect highly qualified, intentional audiences. This is a signal of audience precision, not just content quality.

**Low performance may indicate:** Templates may not be fully personalized for their target segment, or the experience may be receiving unintended traffic. Low visitor counts alone are not a failure signal — Templated Experiences are designed for targeted audiences, not broad reach.

**Guidance:** When Templated Experiences show high per-visitor conversion rates at low volume, call this out as a maturity signal — it means the 1:1 or 1:Few ABM motion is working. Recommend scaling successful templates to new accounts or segments. When Templated Experiences show low engagement, recommend reviewing personalization configuration and content relevance for the target account.

---

### Target

**What it is:** A legacy PathFactory experience type. Delivers personalized content overlays using rule-based targeting logic. Widely used but does not support the full personalization and AI capabilities of modern experience types.

**Strong performance indicates:** The content and targeting rules are well-matched to the audience. High traffic and conversion on Target experiences is a strong signal of demand, but it represents legacy infrastructure serving that demand — not a modern, scalable setup.

**Low performance may indicate:** Targeting rules may be outdated, content may not be refreshed, or the experience format itself may be limiting engagement depth. Zero-conversion Target experiences with high traffic are a strong signal that conversion mechanics (CTAs, gated assets) are missing or misaligned.

**Guidance:** When Target performs well, acknowledge the demand signal but recommend a pathway toward Content Playlists or Templated Experiences for that use case. Do not recommend investing further in Target infrastructure — recommend migrating high-performing Target experiences to modern equivalents to unlock personalization scale and AI capabilities.

---

### Recommend

**What it is:** A legacy PathFactory experience type. Displays a recommendation panel that surfaces additional content to visitors based on simple rules or behavioral signals. Predecessor to modern AI-driven recommendation in Content Playlists.

**Strong performance indicates:** Visitors are motivated to explore beyond their initial content, and the recommendation logic is surfacing relevant assets. Form fills on Recommend experiences suggest the audience is engaged enough to act, even within a legacy format.

**Low performance may indicate:** Recommendation rules are not well-tuned, or the content library lacks the variety needed to serve relevant next-best-content. Very low session times on Recommend experiences suggest visitors are not finding the recommended content relevant.

**Guidance:** Recommend experiences that show high visitor volume but declining engagement or conversion YoY are a clear signal to migrate to Content Playlists, where AI-driven personalization will outperform rule-based recommendations. Use high-performing Recommend experiences as a reference point for what content topics and asset types resonate — and carry those signals into Playlist design.

---

### Microsites

**What it is:** A legacy PathFactory campaign experience. Standalone branded content hubs, typically used for events, ABM campaigns, or industry-specific destinations. Functionally replaced by Templated Experiences.

**Strong performance indicates:** The campaign or event this Microsite supported had strong audience alignment. Engagement and conversion here reflect the quality of the campaign audience, not the scalability of the format.

**Low performance may indicate:** The Microsite may be outdated, the campaign it supported has concluded, or the format itself is limiting reach and personalization. Legacy Microsites do not support dynamic personalization or AI translation.

**Guidance:** Treat active Microsites as migration candidates. If a Microsite is still driving meaningful traffic, recommend rebuilding it as a Templated Experience to unlock AI personalization, translation, and reusability. If it is deactivated or receiving minimal traffic, flag it for retirement.

---

### Interpretation Guidance

Apply the following lenses when generating narrative sections, strengths, opportunities, and recommendations:

- **Buyer journey depth:** Connect engagement metrics (binge rate, session time, views per session) to how far buyers are progressing through a content journey. High binge rates on modern experiences indicate strong journey progression. Low binge rates on high-traffic experiences indicate the journey is not capturing buyers beyond the first touchpoint.

- **Personalization maturity:** Assess whether the experience type being used matches the sophistication of the personalization goal. Target and Recommend experiences indicate early-stage personalization maturity. Content Playlists and Templated Experiences indicate a modern, scalable personalization approach. Frame the mix of experience types as a maturity indicator, not just a performance category.

- **Campaign scalability:** Templated Experiences and Content Playlists support campaign replication at scale. When these are performing well, frame it as a scalability asset — the same motion can be deployed across segments, verticals, or geographies. When legacy types are carrying the bulk of traffic and conversions, flag it as a scalability risk.

- **Modernization opportunities:** When a legacy experience type (Target, Recommend, Microsites) is performing well, do not simply celebrate it. Acknowledge the demand signal, then recommend migrating to the modern equivalent to unlock greater personalization depth, AI capabilities, and scale. Strong legacy performance is a migration opportunity, not a reason to maintain the status quo.

- **Do not treat legacy and modern experiences as equivalent:** When comparing experience types in the executive summary or recommendations, always distinguish between legacy and modern types. A 1.74% form rate on a Target experience and a 13.2% form rate on a Templated Experience are not the same kind of result — one reflects a broad legacy audience, the other reflects a precision-targeted modern campaign.

---

## Ranking Logic

When determining top-performing assets, experiences, or content types, always rank using this priority order:

1. **Conversions first** — form fills, CTA clicks, and downloads are the strongest signal. Rank by total conversions where available.
2. **Engagement second** — if conversion data is tied or unavailable, rank by engagement score, then binge rate, then views per session.
3. **Visitor volume third** — use as a tiebreaker only. High traffic with low engagement and zero conversions is a gap signal, not a win.

Apply this logic consistently across Content Performance (section 4), Content Type Analysis (section 5), Topic Analysis (section 6), and Experience & Time Performance (section 7).

If conversion data is missing for a section, fall back to engagement, state the limitation explicitly, and do not imply conversion performance.

---

## Analysis Coverage

Every report must address all of the following areas using only real data from the parsed files.

---

### 1. Visitor Trends
- Total visitors for the period
- YoY delta overall and by industry
- Top industries by visitor volume
- Industries showing growth vs. decline
- Worst declining industries
- Flag high "Undefined" industry traffic as an attribution risk

---

### 2. Engagement Analysis
- Overall engagement rate and MoM trend
- Binge rate and what it signals
- Views per session and avg session time
- Engagement score distribution across assets
- Depth of content consumption signals

---

### 3. Conversion Quality
- Overall form capture rate, CTA click rate, download rate
- Compare to prior period where data allows
- Top converting experiences
- Zero-conversion experiences with high traffic — flag as gaps
- Which forms are driving conversions (by name/ID if available)
- Which experiences are driving the most conversions
- Which content assets are driving conversions
- Which content types contribute most to conversions

---

### 4. Content Performance
- Top 5 performing content assets by views
- For each: include content type and topic tag if available in the data
- For each: include views, engagement score, form fills, and downloads where available
- Identify assets that are high-traffic but low-conversion (gap signal)
- Identify assets that are low-traffic but high-engagement (underexposed signal)

---

### 5. Content Type Analysis
- Group all assets by content type (e.g. eBook, webinar, one-pager, case study, video)
- Identify which content types drive the most views
- Identify which content types drive the highest engagement scores
- Identify which content types drive the most conversions (form fills, downloads)
- Surface any content type with high volume but low conversion as a gap

---

### 6. Topic Analysis
- If topic tags exist in the data, group assets by topic
- Identify top-performing topics by engagement score
- Identify top-performing topics by conversions
- Note any topics with high traffic but low engagement or conversion
- If topic tags are absent or sparse, flag as a data gap

---

### 7. Experience & Time Performance
- Performance by experience type: Content Playlist, Target, Recommend, Templated, Microsites
- Per type: visitor counts, form rates, download rates, YoY deltas
- Identify best and worst performing experience type
- Top 3 performing individual experiences ranked by combined engagement and conversion signals
- For each top experience: include experience name, type, visitor count, form rate, download rate
- Session time trends and incremental time metrics

---

### 8. Pipeline Influence
- Total form fills, CTA clicks, and downloads as revenue-relevant signals
- S1/S2 pipeline influenced where data is available
- Closed Won attribution where data is available
- Revenue per visitor trend
- YoY trajectory of pipeline influence metrics

---

### 9. Benchmark & Comparative Analysis (Optional)

Only include this section if benchmark or industry benchmark files were found during the validation pass.

- Compare the customer's key metrics against available benchmarks: engagement rate, form capture rate, binge rate, views per session
- Identify where the customer is outperforming the benchmark and by how much
- Identify where the customer is underperforming and flag as a priority gap
- If industry-specific benchmarks are available, use those over company-wide averages
- Label all benchmark figures clearly — state the source (e.g. "company-wide average", "industry benchmark") so the reader understands the comparison basis
- Do not fabricate benchmark figures — if no benchmark file exists, omit this section entirely

Where benchmark comparisons are strong, incorporate them into What's Working. Where the customer underperforms, incorporate into What to Watch or Recommended Next Steps.

---

## Report Structure

Follow this structure exactly. Do not add or remove sections.

### 1. KPI Bar
Display 6 key metrics at the top of the report. Use available data in this order:
1. Total Visitors
2. Engagement Rate
3. Binge Rate
4. Form Capture Rate
5. Total Form Fills
6. CTA Click Rate (fall back to Total Downloads if CTA data is unavailable)

Each metric must show a YoY or period-over-period delta where data allows.

### 2. Executive Summary
Write 3–4 sentences only. Cover:
- Overall performance trend for the period
- The biggest value driver (what's working most)
- The biggest opportunity (what to address)
- At least one specific metric to anchor the narrative

Do not summarize every metric. Do not repeat data that appears in the supporting tables. Write for a VP or CMO — confident, outcome-focused, no jargon.

### 3. Where You're Seeing Value
Exactly 3 strengths. Each must:
- Include a specific data point or metric
- Focus on high-performing content, experiences, or conversion signals
- Explain why it matters as a business outcome
- Reference benchmark performance if benchmark data is available and relevant
- At least one must reflect content performance, content type strength, or a top-performing experience

### 4. Growth Opportunities
1–2 areas for improvement. Each must:
- Be supported by specific data evidence
- Be framed constructively — as an opportunity, not a failure
- Examples: zero-conversion high-traffic experiences, underperforming content types, missing topic coverage, attribution gaps

### 5. Recommended Actions
Exactly 3 actions. Each must be:
- Tied directly to a specific finding from the analysis
- Specific and actionable — not generic advice
- Prioritized by potential impact on engagement, conversion, or pipeline
- At least one must address content or experience optimization

### 6. Strategic Takeaway
One sentence. The single most important insight a CEO could repeat in a meeting.

### 7. Supporting Data Tables
After the narrative, include all relevant data tables as defined in `html-template.md`. The tables carry the detailed data — the narrative should reference key figures but not reproduce full datasets.

### 8. Optional Sections
Include only if data exists:
- Benchmark Comparison table
- Conversion Drivers table
- Data Gaps & Notes

---

## Data Availability Rules

These rules govern how to handle missing, sparse, or ambiguous data. They exist to prevent fabricated insights.

- **Never estimate or infer a metric that is not present in the data.** If a field is blank, zero, or absent, treat it as unavailable — not as zero performance.
- **If a core analysis section cannot be completed** due to a missing file, state clearly in the report: what data was missing, which section was affected, and what could not be assessed as a result.
- **If a metric exists but is sparse** (e.g. topic tags on fewer than 20% of assets), complete the analysis on what is available and flag the coverage gap explicitly.
- **If conversion data is missing at the asset or form level**, fall back to experience-level conversion data. If that is also missing, fall back to aggregate totals. State the fallback level used.
- **Do not combine metrics across incompatible time periods** without noting the mismatch. If one file covers Q1 and another covers full-year, label each figure with its period.
- **Benchmark figures must come from a parsed benchmark file.** Do not use recalled or assumed industry averages.
- **If two files contain conflicting values for the same metric**, flag the conflict, use the more granular or recent source, and note which source was used.

---

## Writing Rules

- Write for a VP or CMO, not a data analyst
- Every number must be interpreted in context — never list raw data
- No jargon — if you use a platform term, briefly explain it
- No vague recommendations — every next step must be traceable to a specific finding
- Connect every metric to a business outcome
- If data is missing for a section, note the gap and explain what it means — do not skip or fabricate
- No single-metric storytelling — always connect multiple signals to tell a complete story
