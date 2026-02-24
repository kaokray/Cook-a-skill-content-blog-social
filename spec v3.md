# SKILL SPEC: Content Pipeline Pro v2
**Owner**: Huỳnh Anh Dương (Kray) | **Domain**: Content Writing / SEO / GEO | **Version**: 2.1

---

## Overview

A complete end-to-end content pipeline that turns a keyword + project spec into a publish-ready, GEO-optimized blog article — enriched with real community voice from UGC. Covers every stage from trend monitoring to final scoring.

**Pipeline stages:**

```
[0] X TREND MONITOR — simulated 24/7, auto-proposes hot keywords on session start
      ↓
[1] KEYWORD RESEARCH — scored, multi-source, data-backed
      ↓
[2] CONTENT BRIEF & OUTLINE — mapped to long-tail keywords + social expansion points
      ↓
[3] UGC ENRICHMENT — mine community comments → ready-to-paste blog sections
      ↓
[4] DRAFT — human-style writing, minimum 3 data points, zero AI patterns
      ↓
[4.5] VISUAL & LINK ENRICHMENT — data charts + inline hyperlinks on every source citation
      ↓
[5] SEO + GEO OPTIMIZATION — on-page checklist + AI-bot-friendly formatting
      ↓
[6] QA SCORING REPORT — rubric-based score, publish verdict
```

---

## User

- **Primary**: Content Writer / SEO Writer
- **Secondary**: Marketing Manager, Social Media Executive
- **Context**: Crypto/Web3 content team shipping blog posts regularly — needs consistent tone, SEO optimization, and content that gets cited by AI search engines (Perplexity, Google SGE, ChatGPT Search)

---

## Input

### Required

| Field | Type | Description | Example |
|---|---|---|---|
| `project_spec` | file (.md) | Product info, target audience, value prop, tone of voice | `spec.md` for Project XYZ |
| `keyword_or_topic` | string | Keyword or topic to write about (can be auto-proposed from Stage 0) | "what is liquid staking" |

### Optional

| Field | Type | Description | Default |
|---|---|---|---|
| `ugc_urls` | list of URLs | X threads, Reddit posts, forums to mine for UGC | None — Stage 3 skipped if absent |
| `blog_draft` | text or URL | Existing draft to cross-reference in UGC stage | None |
| `language` | string | Output language | English |
| `word_count` | number | Desired word count | 1500–2000 |
| `tone` | string | Writing tone | Auto-detected from spec |
| `additional_context` | string | Extra angle or instruction | — |

---

## Stage 0 — X Trend Monitor (Simulated 24/7)

### Purpose
Ensure the writer never misses a trending topic while offline. Every time a new session opens, the skill automatically scans X for hot topics relevant to the project spec — and proposes them before the writer even asks.

### Trigger
**Runs automatically at the start of every new conversation**, before the user types anything else. No manual command needed.

### How It Works

**Step 1 — Parse the spec**
Read `project_spec.md` to extract:
- Domain / niche (e.g., DeFi, liquid staking, perp DEX)
- Target audience
- Key product themes and competitors

**Step 2 — Run X trend searches**
Use web search to simulate real-time X monitoring. Run all of the following:

```
site:x.com [domain keyword] -filter:replies
[domain keyword] trending twitter 2025
[domain keyword] discussion OR debate OR thread twitter
[competitor name] twitter sentiment 2025
[domain keyword] viral tweet this week
```

For crypto/Web3 specifically, also search:
```
crypto twitter trending today
defi twitter hot topic this week
[domain keyword] CT (crypto twitter) discussion
```

**Step 3 — Score each topic by trending potential**

| Signal | Weight | Scoring |
|---|---|---|
| Recency (posted within 48h) | 30% | Within 24h = 10, 24–48h = 7, older = 3 |
| Estimated engagement | 30% | Viral (1K+ likes signals) = 10, high = 7, low = 3 |
| Relevance to spec domain | 25% | Direct = 10, adjacent = 6, weak = 2 |
| Debate / controversy signal | 15% | Active debate = 10, one-sided = 5, none = 2 |

**Step 4 — Output trend alert**

Present at session start, before any user input:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔥 X TREND ALERT — [Date/Time]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Based on your project spec, here's what's hot on X right now:

TREND 1 (Score: X/10) 🔴 HOT
  Topic:       [topic name]
  Why it's trending: [1-sentence explanation]
  Angle for your blog: [specific content angle]
  Suggested keyword: "[keyword]"
  Sample X discussion: "[paraphrased post or thread summary]"

TREND 2 (Score: X/10) 🟡 RISING
  Topic:       [topic name]
  Why it's trending: [1-sentence explanation]
  Angle for your blog: [specific content angle]
  Suggested keyword: "[keyword]"

TREND 3 (Score: X/10) 🟢 WATCH
  Topic:       [topic name]
  Why it's trending: [1-sentence explanation]
  Angle for your blog: [specific content angle]
  Suggested keyword: "[keyword]"

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
→ Want to write about one of these? Just say "go with Trend 1"
  and I'll start the pipeline from Stage 1 automatically.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### Limitations
- This is simulated monitoring via web search — not a real-time API connection to X
- Results reflect what search engines have indexed from X, not live X data
- If web search is disabled, skip Stage 0 and flag: "Stage 0 unavailable — web search is off. Please provide a keyword manually."

---

## Stage 1 — Keyword Research

### Goal
Identify 1 primary keyword + 5–10 secondary/LSI keywords with real data and scoring — not random picks.

### Step 1 — Generate seed keywords
Brainstorm 8–12 candidate keywords from the topic:
- Head terms (1–2 words)
- Mid-tail (3–4 words)
- Long-tail / question variants (5+ words: "how to...", "best...", "what is...")

### Step 2 — Fetch Google Trends data
For each seed keyword, run web searches:
- `google trends [keyword] 2025` → trend direction (rising / stable / declining)
- `[keyword] search interest 2025`

Extract: trend direction, estimated score (0–100), seasonal pattern.

### Step 3 — Fetch X social buzz
For each seed keyword, run:
- `site:x.com [keyword]`
- `[keyword] trending twitter 2025`
- `[keyword] discussion reddit OR twitter OR forum`

Extract: buzz level (High/Medium/Low), what people are actually debating, notable angles.

### Step 4 — Fetch search volume signals
Run free-source searches to estimate volume:
- `[keyword] search volume 2025`
- `ubersuggest [keyword]` or `semrush [keyword]` for visible free-tier data
- Google "People Also Ask" for [keyword] → extract as long-tail candidates
- Google "Related searches" for [keyword] → extract additional candidates

Label all estimated data as `[estimated]`.

> If user has Ahrefs/SEMrush API key: ask once — "Do you have an Ahrefs or SEMrush API key for exact volume data?" If yes, use it. If no, proceed with estimated data.

### Step 5 — Score and rank keywords

| Signal | Weight | Scoring |
|---|---|---|
| Search volume | 35% | <100=2, 100–1K=4, 1K–10K=7, 10K+=10 |
| Keyword difficulty (inverse) | 30% | Low=10, Medium=6, Hard=3 |
| Google Trends direction | 20% | Rising=9, Stable=6, Declining=2 |
| X/Social buzz | 15% | High=9, Medium=5, Low=2 |

Pick top 1 as primary, next 5–8 as secondary/LSI.

### Output

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
KEYWORD RESEARCH RESULTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

PRIMARY KEYWORD (Score: X/10)
  Keyword:       [keyword]
  Volume:        [X/month — estimated]
  Difficulty:    [Low/Medium/Hard]
  Trend:         [Rising📈 / Stable➡️ / Declining📉]
  X Buzz:        [High/Medium/Low] — "[what people are actually debating]"
  Search Intent: [Informational/Navigational/Transactional/Commercial]

SECONDARY KEYWORDS:
┌─────────────────────────┬────────┬──────┬────────────┬──────────┬───────┐
│ Keyword                 │ Volume │  KD  │ Trend      │ Buzz     │ Score │
├─────────────────────────┼────────┼──────┼────────────┼──────────┼───────┤
│ [keyword 1]             │ [est.] │ [KD] │ Rising📈   │ High     │  X.X  │
│ [keyword 2]             │ [est.] │ [KD] │ Stable➡️   │ Medium   │  X.X  │
│ ...                     │        │      │            │          │       │
└─────────────────────────┴────────┴──────┴────────────┴──────────┴───────┘

KEY INSIGHT FROM SOCIAL DATA:
"[What people are actually debating/asking on X/forums]"
→ Use this as the hook in the intro and FAQ section.

CONTENT ANGLE RECOMMENDATION:
[1–2 sentences on the unique angle based on trending signals + content gap]
```

---

## Stage 2 — Content Brief & Outline

### Goal
Build a logically sequenced outline that follows the reader's mental journey, maps every long-tail keyword to a section, and flags where UGC enrichment (Stage 3) will be inserted.

### Step 1 — Determine flow pattern

| Pattern | When to use | Arc |
|---|---|---|
| Problem → Solution | How-to, guides | Problem → Why → Solution → Validation |
| What → Why → How | Explainers | Definition → Importance → Application |
| Comparison | Best X, X vs Y | Context → Criteria → Options → Recommendation |
| Journey | Beginner guides | Starting point → Stages → End state |
| Argument | Opinion, trends | Claim → Evidence → Counter → Conclusion |

### Step 2 — Map long-tail keywords to sections
Assign each long-tail keyword to a specific H2 or H3. No section without a keyword anchor. Build a mapping table before writing the outline.

### Step 3 — Flag UGC insertion points
For each major H2, identify where community voice adds depth:
- Common misconceptions debated on X → add "Community Perspectives" H3
- Recurring user questions → convert to FAQ entry
- Real user experiences → flag for Stage 3 UGC mining

### Output

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CONTENT BRIEF
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Target Keyword:     [primary keyword]
Flow Pattern:       [chosen pattern]
Search Intent:      [type]
Recommended Length: [X words]
Target Audience:    [who, what they know, what they need]
Content Goal:       [rank / educate / convert / build trust]
GEO Target:         AI search engines (Perplexity, Google SGE, ChatGPT Search)

LONG-TAIL KEYWORD MAP:
[keyword 1] → H2: [section title]
[keyword 2] → H3: [subsection title]
[keyword 3] → FAQ: [question form]

UGC INSERTION POINTS (flagged for Stage 3):
[Section X] ← UGC: community counterpoints
[Section Y] ← UGC: real user experiences / case studies
[FAQ]       ← UGC: real questions from X/Reddit threads

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
OUTLINE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

H1: [Title — primary keyword + compelling angle]

── INTRO ──────────────────────────────────
  Hook:    [specific stat or bold claim — never a generic opener]
  Problem: [what the reader is struggling with]
  Promise: [what this article delivers]

── BODY ───────────────────────────────────
H2: [Section 1]                                    🔑 [keyword]
  H3: [Subsection A]
  H3: [Subsection B]
  H3: 💬 UGC BLOCK — [community counterpoints]     ← Stage 3 insertion

H2: [Section 2]                                    🔑 [keyword]
  H3: [Subsection A]
  H3: 💬 UGC BLOCK — [real user experiences]       ← Stage 3 insertion

[... continue for all mapped keywords ...]

── FAQ ────────────────────────────────────
H2: Frequently Asked Questions
  H3: [Question from long-tail keyword]?           🔑 [keyword]
  H3: [Question from X/Reddit community]?          💬 UGC source

── CONCLUSION ─────────────────────────────
  Summary: [2–3 key takeaways]
  Takeaway: [the one thing to remember]
  CTA: [specific next action]

KEYWORD COVERAGE CHECK:
  Primary keyword:    H1 ✓ | Intro ✓ | H2 ✓ | Conclusion ✓
  Long-tail keywords: [list each → assigned section ✓]
  Unplaced keywords:  [list → decide: add section or cut]
```

---

## Stage 3 — UGC Enrichment

### Purpose
Mine real community comments from X threads, Reddit, and forums → transform them into ready-to-paste blog sections that add authentic human voice. This is the layer that separates this content from AI slop — and the key signal that gets cited by AI search engines.

**Why this matters for GEO:**
Reddit alone accounts for ~21% of citations in Google AI Overviews (early 2026). Content with real UGC gets 2–3x more visibility than theory-only articles. E-E-A-T's "Experience" signal is the one thing AI-generated content fundamentally cannot fake.

### Trigger
Runs when `ugc_urls` are provided. If no URLs given, skip this stage and note: "Stage 3 skipped — no UGC URLs provided. Add X/Reddit links for community enrichment."

### Step 1 — Fetch and extract comments
For each URL:
- Use `web_fetch` to retrieve the full page content
- Extract: original post body, all comments/replies with engagement metrics (likes, upvotes, reply count), timestamp, nesting level
- Fallback: if URL is behind a login wall → "Could not access [URL]. Paste comment text directly and I'll process it."

### Step 2 — Quality scoring (0–10)

| Signal | Weight | Scoring |
|---|---|---|
| Engagement (likes/upvotes) | 30% | Top 10% = 10, top 25% = 7, top 50% = 5, bottom 50% = 2 |
| Content length | 20% | <10 words = 1, 10–50 = 5, 50–150 = 8, 150+ = 10 |
| Contains data/numbers | 15% | Yes = 10, No = 3 |
| Personal experience markers | 15% | "I tried...", "In my case..." = 10, None = 3 |
| Substantive reply thread | 10% | 3+ quality replies = 10, 1–2 = 6, none = 3 |
| Sentiment strength | 10% | Strong opinion = 8, Neutral = 4 |

Filter: Score ≥ 6 → High Value. Score < 3 → Discard (spam, memes, off-topic).

### Step 3 — Classify into 3 UGC categories

**Category A — Counter-Arguments & Alternative Perspectives**
Challenges the main article claims, edge cases, overlooked downsides.
Output: 150–300 word prose paragraph, balanced tone, titled "Community Perspectives: Notable Counterpoints"

**Category B — Real-World FAQs**
Direct questions from comments, especially highly-upvoted or repeated ones.
Output: Q&A pairs (3–6 max), answers synthesized from community + AI knowledge. Uncertain answers flagged with ⚠️ [Verify before publishing]

**Category C — Personal Experiences & Mini Case Studies**
First-person accounts with specific numbers, before/after narratives, warnings from experience.
Output: 2–4 mini case studies, each 50–100 words, professionally paraphrased — never fabricated.
Format:
```
**[Descriptive title]**
[Paraphrased experience preserving original details and specifics]
— Source: [Platform] user | Engagement: [X likes/upvotes]
```

**Never:**
- Fabricate comments or data points not in the source
- Include real usernames — use "a user on X", "a Reddit commenter"
- Include spam, memes, or personal attacks even if highly upvoted

### Step 4 — Viral pattern analysis
For each high-value comment (score ≥ 7), identify why it resonated:

| Trigger | Description |
|---|---|
| Data-backed claim | Specific numbers, dollar amounts |
| Contrarian take | Opposes popular opinion with reasoning |
| Personal vulnerability | Shares failure or honest struggle |
| Insider knowledge | Suggests expertise or access |
| Simplification | Breaks down complexity clearly |

Output: Top 3 viral triggers + 2 actionable writing tips derived from patterns.

### Step 5 — Map UGC blocks to outline
Match each UGC block to the insertion points flagged in Stage 2 outline.

### Output format

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
UGC ENRICHMENT REPORT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Sources: [X] URLs | Total comments: [X] | High-value: [Y] ([Z]%)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SECTION A: COMMUNITY PERSPECTIVES — NOTABLE COUNTERPOINTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[150–300 word prose — ready to copy-paste into blog]
→ INSERT AFTER: [H2 section from outline]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SECTION B: FAQ — REAL QUESTIONS FROM THE COMMUNITY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Q1: [Real question — paraphrased]
A1: [Answer synthesized from community + AI knowledge]
    Source: [X] users asked this | Top answer: [Y] upvotes
→ INSERT INTO: FAQ section

[... up to Q6 ...]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SECTION C: REAL USER EXPERIENCES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CASE 1: [Descriptive title]
[Paraphrased experience — professional tone, original details preserved]
— Source: [Platform] user | [X] likes/upvotes
— Viral trigger: [why this resonated]
→ INSERT AFTER: [H2 section from outline]

[... up to CASE 4 ...]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
VIRAL PATTERN ANALYSIS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Top triggers: 1. [type] — [X] comments | 2. [type] | 3. [type]
Writing tips:
→ [Tip 1 based on dominant pattern]
→ [Tip 2]
```

---

## Stage 4 — Draft Writing

### Goal
Write the full article following the outline, with UGC blocks inserted at flagged points. Human-style, data-backed, zero AI patterns.

### Writing Principles

**Structure**
- Intro: Hook (stat/bold claim/specific fact — never a generic opener) → Problem → Promise
- Body: Follow outline exactly. Each H2 opens with a topic sentence. UGC blocks inserted at flagged points.
- Conclusion: Synthesize key takeaways (do not restate all H2s) → clear CTA

**Tone (default for crypto/Web3)**
- Expert-to-peer: assumes reader knows basic crypto, not a developer
- Direct and confident — no hedging
- Short sentences preferred; vary length for rhythm
- Define technical terms inline on first use
- Use "you" to address the reader directly

**Data requirements**
- Minimum 3 data points per article (stats, on-chain figures, market numbers)
- Source every stat inline: `[stat] — [Source, Year]`
- Find real stats via web search before drafting: `[topic] statistics 2025`, `[topic] data report 2025`
- If no real data found: insert `[DATA NEEDED: search "[suggested query]"]` — never invent statistics

**AI-pattern avoidance — never write:**
- "In today's fast-paced world..." / "In the realm of..."
- "It's important to note that..." / "It goes without saying..."
- "Furthermore," / "Moreover," / "In conclusion,"
- "Delve into" / "Dive into" / "Leverage" (abstract)
- "As we navigate the ever-evolving landscape of..."
- "Game-changer" / "Revolutionary" / "Transformative" / "Comprehensive"
- Rhetorical openers: "Have you ever wondered...?"
- "Not only... but also..." / "Both... and..." (overused)
- Bullet dashes (`- item`) or em dashes (`X — Y`) → use numbered lists or rewrite as sentences
- Conclusion openers: "In conclusion," / "To summarize," / "We hope this article..."

Instead: open every section with a direct statement or specific fact. Let data carry the weight.

**Keyword integration**
- Primary keyword in first 100 words, at least one H2, and conclusion
- Secondary/LSI keywords woven in naturally — never forced
- Target density: 1–1.5% for primary keyword

---

## Stage 4.5 — Visual & Link Enrichment

### Goal
Transform the raw draft into a visually credible, citation-verified document by: (1) generating data charts for every key statistic, and (2) converting every source attribution in the text into a live, clickable hyperlink pointing to the original article.

Runs automatically after Stage 4 draft is complete. Cannot be skipped — these two elements are required for publish-ready output.

### Why This Matters
- **Charts**: Data presented as a graph is 3× more likely to be cited by AI search engines than the same data presented as plain text. Charts also reduce bounce rate and add E-E-A-T visual authority.
- **Hyperlinks**: Inline links on source citations signal editorial credibility to Google and AI crawlers. Every unlinked "— Source, Year" is a missed trust signal.

---

### Step 1 — Identify All Chart Opportunities

Scan the draft for data points that qualify for chart conversion. A data point qualifies if it meets **at least one** of these criteria:

| Criterion | Example |
|---|---|
| Shows change over time (2+ time periods) | "BTC fell from $126K to $65K over 5 months" |
| Compares two or more assets/metrics | "Gold +64% vs Bitcoin −42% in 2025" |
| Shows a trend or flow (inflows/outflows) | "$8.5B ETF outflows since October" |
| Represents a scored index or rating | "Fear & Greed Index: 5/100" |
| Shows a ratio that changed | "38 oz gold per BTC → 13 oz in 14 months" |
| Contains 3+ data points in a series | Monthly correlation figures across a year |

**Chart types to use:**

| Data type | Chart type |
|---|---|
| Performance over time | Line chart with fill-under |
| Inflows / outflows | Bar chart, green = positive, red = negative |
| Index or score over time | Bar chart with color-coded zones |
| Ratio or comparison over time | Line chart or area chart |
| Single-point comparison | Horizontal bar or stat callout box |

**Chart design standards (apply to every chart):**
- Background: `#F7F7F7` (light gray), no heavy gridlines
- Primary color: match brand (default orange `#E8650A` for crypto/Web3)
- Spine: remove top + right
- Labels: annotate key data points directly on the chart (peak, trough, threshold)
- Source line: always include at bottom-left in gray italic — `Source: [Name] | [Data notes]`
- Font: DejaVu Sans (system default for matplotlib)
- Resolution: 150 DPI minimum
- Alt text: always generate a plain-English alt text description for every chart

**Maximum charts per article:** 6. More than 6 charts makes the document heavy and slows page load.

**If no qualifying data points found:** output a styled stat callout box instead of a chart for that statistic.

---

### Step 2 — Generate Charts

Use Python + matplotlib to generate each chart as a PNG file. Execute chart generation code in the computing environment.

For each chart generated, produce:
1. The PNG image embedded in the output document
2. A plain-English caption (1–2 sentences, starts with "Chart X:", states what the chart shows and source)
3. An alt text string (for CMS upload): describes the chart for screen readers and Google image indexing

**Caption format:**
```
Chart [N]: [What it shows]. [Time period if applicable]. Sources: [Name 1], [Name 2].
```

**Alt text format:**
```
[Chart type] showing [metric] from [start] to [end]. [Key finding in one sentence].
```

---

### Step 3 — Insert Charts at Correct Positions

Each chart must be placed **immediately after** the paragraph that introduces the data it visualizes — not at the end of the section.

Chart placement rules:
- Never place a chart before its first textual reference
- Never stack two charts back-to-back without body text between them
- Place chart + caption + alt text as a unit — never split
- If a chart covers data from multiple sections, place it at the section where it is most relevant

---

### Step 4 — Convert All Source Citations to Hyperlinks

Scan the entire draft for every inline source citation. A source citation is any of these patterns:

| Pattern | Example |
|---|---|
| `— [Source, Year]` | `— CoinDesk, Jan 2026` |
| `per [Source]` | `per Bloomberg` |
| `according to [Source]` | `according to Fortune` |
| `[Source] reports` | `Deutsche Bank reports` |
| `[Source] analysis` | `KuCoin analysis` |
| `([Source])` | `(CoinDesk)` |

**For each citation found:**

1. Run a web search to find the specific article: `[publication name] [topic] [approximate date]`
2. Verify the article exists and the URL resolves
3. Replace the plain-text source mention with an inline hyperlink
4. Use the source name as the anchor text (e.g., `Fortune`, `CoinDesk`)
5. If the exact article cannot be found: link to the publication's homepage and flag `[VERIFY URL]`

**Link quality rules:**
- Never link to paywalled articles if a free version exists elsewhere
- Prefer the original publisher over aggregators
- All external links: open in new tab in HTML output
- Do not add links to unattributed claims — flag these `[SOURCE NEEDED]`

---

### Step 5 — Output Summary

After completing Steps 1–4, append this summary to the draft:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STAGE 4.5 — VISUAL & LINK ENRICHMENT SUMMARY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Charts generated:    [N] / [max 6]
  - Chart 1: [title] → placed after [section name]
  - Chart 2: [title] → placed after [section name]

Source links resolved: [N] / [total citations found]
  - [Source name] → [URL] ✅
  - [Source name] → [URL] ⚠️ [VERIFY URL — linked to homepage]

Unlinked citations flagged: [N]
  - "[stat or claim]" → [SOURCE NEEDED]

Alt text strings:
  Chart 1: "[alt text]"
  Chart 2: "[alt text]"
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

### Edge Cases for Stage 4.5

| Case | Handling |
|---|---|
| Data point has no clear chart type | Use a styled stat callout box instead |
| More than 6 chart-worthy data points | Prioritize: (1) comparisons, (2) trends, (3) index scores. Remainder → stat callout boxes |
| Source URL is paywalled | Search for free version (Google Cache, archive.org). If not found: link to homepage + `[VERIFY URL]` |
| Source article cannot be found | Link to publication homepage + `[SOURCE NEEDED — could not verify]` |
| Citation is vague ("analysts say") | Flag `[SOURCE NEEDED]` — do not invent a source |
| Chart data conflicts with text | Flag `[DATA DISCREPANCY — check source]` and leave both for human review |
| Web search unavailable | Skip link resolution. Flag all citations `[HYPERLINK NEEDED — web search off]`. Charts still generated from in-draft data. |

---

## Stage 5 — SEO + GEO Optimization

### SEO On-Page Checklist

**Title & Meta**
- [ ] Meta title: 50–60 characters, primary keyword near the front
- [ ] Meta description: 150–160 characters, primary keyword, includes hook/CTA
- [ ] URL slug: short, lowercase, hyphenated, primary keyword

**Content Structure**
- [ ] H1 contains primary keyword (only one H1)
- [ ] H2s use secondary keywords or question variants
- [ ] Primary keyword in first 100 words
- [ ] Primary keyword in conclusion
- [ ] Word count meets brief recommendation

**Keyword Usage**
- [ ] Primary keyword density: 1–1.5%
- [ ] No keyword stuffing
- [ ] LSI/semantic keywords distributed throughout
- [ ] 2–3 long-tail variants used

**Readability**
- [ ] Paragraphs: max 3–4 lines
- [ ] No walls of text
- [ ] Bullet/numbered lists used where appropriate

**Links**
- [ ] 2+ internal link suggestions noted
- [ ] 1–2 authoritative external sources noted
- [ ] Image alt text recommendations included

**Schema Opportunities**
- [ ] FAQ section → FAQ schema
- [ ] How-to steps → HowTo schema
- [ ] Data points present → E-E-A-T signals

---

### GEO Optimization (AI-Bot-Friendly Content)

GEO = Generative Engine Optimization. The goal is to make this content easy for AI agents (Perplexity, Google SGE, ChatGPT Search, future autonomous agents) to parse, extract, and cite.

#### GEO Writing Rules

**1. Answer-first structure (every section)**
Each H2 section must start with a 1–2 sentence direct answer to the implied question — before any elaboration.
```
✅ "Liquid staking lets users stake ETH while keeping their tokens liquid. Unlike traditional staking, you receive a receipt token (like stETH) that can be used across DeFi protocols."
❌ "When it comes to liquid staking, there are several important aspects to consider..."
```

**2. Explicit entity labeling**
Name entities clearly so AI can extract them into knowledge graphs:
- Product names, protocol names with full context on first mention
- Numbers with units always spelled out: "3.2% APY" not "3.2%"
- Dates explicitly stated: "as of Q1 2025" not "recently"

**3. FAQ section is mandatory**
Minimum 5 Q&A pairs. Each answer must be:
- Self-contained (understandable without reading the rest of the article)
- 50–150 words maximum per answer
- Starts with a direct answer, then elaborates

**4. Structured data suggestions (include in QA report)**
Flag which schema types apply:
```
SUGGESTED STRUCTURED DATA:
- FAQPage schema → apply to FAQ section
- Article schema → apply to full post (datePublished, author, headline)
- HowTo schema → apply if article contains step-by-step instructions
- BreadcrumbList → apply for site navigation signals
```

**5. Answer box optimization**
For the primary keyword, write one "featured snippet candidate" block:
- 40–60 word definition or step-list
- Placed early in the article (within first H2)
- Formatted as a clear paragraph OR numbered list (not mixed)

**6. Citation-friendly formatting**
- Every factual claim on its own sentence (not buried in a compound sentence)
- Data points formatted consistently: `[number] [unit] — [Source, Year]`
- No pronoun ambiguity: always name the subject explicitly
- Use `<table>` comparisons where possible — AI agents parse tables well

**7. Internal link structure note**
Suggest 2–3 internal links with anchor text that includes secondary keywords — this signals topical authority to both Google and AI crawlers.

#### GEO Output Block (added to QA Report)

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
GEO OPTIMIZATION CHECKLIST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Answer-first structure (each H2):    ✅/❌
Explicit entity labeling:            ✅/❌
FAQ section present (min 5 Q&A):     ✅/❌
Featured snippet candidate block:    ✅/❌ [paste block here]
Citation-friendly formatting:        ✅/❌
Structured data suggestions:
  - FAQPage schema:                  ✅ applicable
  - Article schema:                  ✅ applicable
  - HowTo schema:                    ✅/❌ [applicable if how-to steps present]
UGC sections present (E-E-A-T):      ✅/❌ [X sections from Stage 3]
AI-bot parse score:                  [X/10]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Stage 6 — QA Scoring Report

### SEO Score Rubric (100 points)

| Check | Points | How to evaluate |
|---|---|---|
| Primary keyword in meta title | 10 | Exact or close match |
| Primary keyword in H1 | 10 | Exact or close match |
| Primary keyword in first 100 words | 10 | Check introduction |
| Keyword density (1–1.5%) | 15 | Count occurrences / total word count |
| Meta title length (≤60 chars) | 10 | Count characters |
| Meta description length (≤160 chars) | 10 | Count characters |
| H2/H3 structure present and logical | 10 | Min 3 H2s, logical flow |
| Image alt text suggestions | 5 | Min 2 suggestions |
| Internal linking suggestions | 10 | Min 2 suggestions |
| Readability (short paragraphs) | 10 | No paragraph >5 lines |

**Thresholds:**
- 85–100: Publish-ready
- 70–84: Minor fixes needed
- Below 70: Needs revision

### Full Report Output

```
╔══════════════════════════════════════════════╗
║       CONTENT PIPELINE PRO — QA REPORT       ║
╚══════════════════════════════════════════════╝

ARTICLE: [Title]
KEYWORD: [Primary keyword]
WORD COUNT: [X words]
UGC SECTIONS: [X sections from Stage 3]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SEO SCORE: [X/100]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

| Check | Points | Status | Details |
|-------|--------|--------|---------|
| Primary keyword in meta title | 10 | ✅/❌ | [details] |
| Primary keyword in H1 | 10 | ✅/❌ | [details] |
| Primary keyword in first 100 words | 10 | ✅/❌ | [details] |
| Keyword density (1–1.5%) | 15 | ✅/❌ | [X%] |
| Meta title length (≤60 chars) | 10 | ✅/❌ | [X chars] |
| Meta description length (≤160 chars) | 10 | ✅/❌ | [X chars] |
| H2/H3 structure | 10 | ✅/❌ | [details] |
| Image alt text suggestions | 5 | ✅/❌ | [details] |
| Internal linking | 10 | ✅/❌ | [details] |
| Readability | 10 | ✅/❌ | [details] |

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
GEO SCORE: [X/10]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[GEO checklist block from Stage 5]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
WRITING QUALITY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
AI patterns detected: [count] — [list with location]
Tone consistency: [Consistent / Flags: section X drifts]
Fact-check flags: [list claims marked [VERIFY]]
Data points present: [X] — [meets/below minimum of 3]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
FINAL VERDICT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SEO:        [Publish-ready / Minor fixes / Needs revision]
GEO:        [Strong / Needs improvement]
UGC:        [Enriched / Missing — add Stage 3 URLs]
Verdict:    [Publish-ready / Minor fixes / Needs revision]

Key actions before publish:
1. [Action 1]
2. [Action 2]
```

---

## Edge Cases

| Case | Handling |
|---|---|
| Keyword too broad (e.g., "crypto") | Stop. Suggest 3–5 long-tail alternatives. Ask user to choose before continuing. |
| Spec file missing info | Use defaults. Flag every assumption with `[ASSUMED]`. |
| Keyword doesn't match spec | Warn about mismatch. Ask for confirmation before continuing. |
| Article needs deep technical content | Flag sections with `[SME REVIEW]`. Never fabricate technical details. |
| User requests Vietnamese | Switch all output to Vietnamese. Keep all formats identical. |
| Word count <500 or >5000 | Warn. Recommend 800–2500 for this topic type. |
| SEO score below 70 | Mark "Needs revision". List specific fixes with section references. |
| Web search unavailable | Flag each stage that requires it. Skip Stage 0. Fall back to training knowledge and label `[estimated]`. |
| UGC URL behind login wall | Skip URL. Request user to paste comment text directly. |
| No high-value comments found (all score <3) | Return: "No high-value comments in this thread. Try a different URL with more substantive discussion." |
| <10 comments total | Process all. Add warning: "Limited comment data — insights may not be representative." |
| Stage 0 finds no trending topics | Return: "No strong trending signals found for your domain right now. Suggest running keyword research on [3 evergreen topics from spec]." |
| Stage 4.5: no chart-worthy data in draft | Output stat callout boxes for all key numbers. Flag: "No time-series or comparison data found — consider adding benchmark data in Stage 4 revision." |
| Stage 4.5: all source URLs paywalled | Link to publisher homepages. Flag every instance with `[VERIFY URL]`. List all in enrichment summary. |

---

## Limitations (MVP)

- Stage 0 is simulated monitoring via web search — not a live X API connection
- Keyword volume data is estimated unless user provides API key
- Does not connect to SEMrush/Ahrefs APIs automatically
- Does not publish to any CMS
- Generates charts from in-draft data (matplotlib); does NOT generate decorative/editorial images
- `[VERIFY]`, `[DATA NEEDED]`, `[SOURCE NEEDED]`, and `[VERIFY URL]` flags require human review before publishing
- SEO/GEO scores are based on internal rubric, not third-party tools
- UGC only covers publicly accessible pages

---

## Success Metrics

| Metric | Before (Manual) | After (Skill) | Improvement |
|---|---|---|---|
| Time per blog article | 4–8 hours | 15–25 minutes | ~85% faster |
| Missed trending topics | High (offline = miss) | Auto-proposed on session start | Near zero |
| UGC enrichment | 1–2 hours manual hunting | 2 minutes automated | ~95% faster |
| Output consistency | Depends on writer | Same format every time | Consistent |
| GEO optimization | Never done | Built into every article | 100% coverage |
| AI citation potential | Low (generic content) | High (E-E-A-T + GEO signals + charts) | Significant |
| Data visualization | 0 (manual, skipped) | 4–6 charts auto-generated per article | 100% coverage |
| Source hyperlinking | Inconsistent / skipped | 100% of citations linked to source URLs | 100% coverage |
| Scale capacity | 1–2 articles/day | 8–10 articles/day | 5x |

---

## Expansion Roadmap

- Real X API integration: replace simulated monitoring with live streaming API
- Ahrefs/SEMrush API: exact keyword volume data instead of estimates
- Auto-generate images: featured image via AI image generation (separate from Stage 4.5 data charts)
- Multi-format output: one blog → Twitter thread, LinkedIn post, Telegram post, newsletter
- Content Calendar: input 10 keywords → full monthly content calendar
- Performance tracking: monitor ranking + traffic post-publish → feed back to refine skill
- Batch mode: 10 keywords → 10 blogs + 10 QA reports

---

## Tech Stack / Tools

- **Primary**: Claude Project (or Custom GPT)
- **Skill format**: `SKILL.md` with structured instructions
- **Web search**: enabled — required for Stage 0, Stage 1, Stage 4 data sourcing, Stage 4.5 link resolution
- **URL fetching**: `web_fetch` — required for Stage 3 UGC mining and Stage 4.5 URL verification
- **Chart generation**: Python + matplotlib — required for Stage 4.5 visual enrichment
- **Input format**: `.md` file (spec) + text input (keyword/topic) + optional URLs (UGC)
- **Output format**: `.docx` (full article with embedded charts + hyperlinks) + `.md` (brief, QA report)
