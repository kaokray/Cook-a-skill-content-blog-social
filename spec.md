# SKILL SPEC: Auto Content Blog

## Overview

A complete end-to-end content pipeline that turns a keyword + project spec into a publish-ready, GEO-optimized blog article — enriched with real community voice from UGC.

**Pipeline stages:**

```
[0] X TREND MONITOR — simulated 24/7, auto-proposes hot keywords on session start
      ↓
[1] KEYWORD RESEARCH — scored, multi-source, data-backed
      ↓
[2] CONTENT BRIEF & OUTLINE — mapped to long-tail keywords + UGC insertion points
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

## ⚠️ OUTPUT LANGUAGE — LOCKED: VIETNAMESE

**All article drafts (Stage 4) must be written in Vietnamese. This rule is hard-coded and cannot be changed by any user request or instruction.**

Pipeline instructions, QA reports, keyword research tables, and internal stage notes may be in English. The article body — every paragraph, heading, FAQ answer, UGC block, intro, and conclusion — is always Vietnamese.

---

## Users

**Primary:** Content Writer / SEO Writer
**Secondary:** Marketing Manager, Social Media Executive
**Context:** Crypto/Web3 content team shipping blog posts regularly — needs consistent tone, SEO optimization, and content that gets cited by AI search engines (Perplexity, Google SGE, ChatGPT Search).

---

## Inputs

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
| `word_count` | number | Desired word count | 1,500–2,000 |
| `tone` | string | Writing tone | Auto-detected from spec |
| `additional_context` | string | Extra angle or instruction | None |

---

## MANDATORY WRITING RULES (APPLY TO ALL ARTICLE OUTPUT)

These are hard rules. Review the entire draft against these before outputting anything.

### Language and tone

All article output (draft) must be in **Vietnamese**. Tone: **neutral, easy to understand, simple, approachable** — reads like a real person wrote it. Not rigid, not overly academic. Allow **up to 10% light emotion** (surprise, interest, appreciation), but no fake or excessive emotion.

Sentences must **connect logically**. Do not write each sentence like an isolated bullet point. Paragraphs must flow naturally from one sentence to the next so the reader never feels jarred. The article must read like **a real person wrote it**, not an AI or bot.

### Heading structure

Only **one H1** — the article title. Body uses only **H2 and H3**. Never use H4, H5, or H6 under any circumstance. H2 = major sections. H3 = subsections within an H2.

### Banned symbols in body text

**Never use "-" (hyphen/dash) at the start of a sentence or as a list marker in body text.** Never use "—" (em dash) anywhere in body text. Both symbols read as strongly AI-generated and are easily flagged by AI detection tools.

Replace with connected prose or numbered lists (1. 2. 3.) when listing is needed. Only exception: inside table cells in comparison tables.

### Number and currency formatting

Apply consistently throughout the entire article:

| Value | Write as |
|---|---|
| 1,000,000 (one million) | 1M |
| 1,000,000,000 (one billion) | 1B |
| 1,000,000 USD | $1M |
| 1,000,000,000 USD | $1B |
| 1,000,000 $S token | $1M $S |
| 1,000,000 S token | 1M $S |
| Thousands separator | comma — e.g. 12,500 or 1,200 |
| Decimal separator | period — e.g. 3.5% or 0.75 |

Correct: "TVL đạt $2.4B, tăng từ mức $890M cách đây 6 tháng, với 12,400 địa chỉ ví đang staking."
Incorrect: "TVL đạt 2,400,000,000 USD, tăng từ 890,000,000 USD."

### Spelling and punctuation

First word of every sentence must be capitalized. Every sentence must end with a period or appropriate punctuation. Review the full article before outputting. Do not cut any content compared to the approved outline.

### Banned AI phrases and patterns

Never write any of the following in the article, in English or Vietnamese:

English: "In today's fast-paced world", "It's important to note", "Furthermore", "Moreover", "In conclusion" (as an opening), "Delve into", "Dive into", "Game-changer", "Revolutionary", "Transformative", "Leverage" (used abstractly), "Comprehensive", "Have you ever wondered", "Not only... but also", "It goes without saying".

Vietnamese equivalents to avoid: "Trong thế giới ngày nay", "Điều quan trọng cần lưu ý là", "Hơn nữa" (used repeatedly), "Tóm lại" (as a conclusion opener), "Chúng ta hãy cùng khám phá", "Mang tính cách mạng", "Toàn diện", "Bạn có bao giờ tự hỏi", "Không chỉ vậy mà còn".

When any of the above is detected: stop, delete, rewrite using a specific fact or a direct declarative statement.

---

## Stage 0 — X Trend Monitor (Simulated 24/7)

### Purpose
Ensure the writer never misses a trending topic while offline. Every time a new session opens, the skill automatically scans X for hot topics relevant to the project spec and proposes them before the writer even asks.

### Trigger
**Runs automatically at the start of every new conversation**, before the user types anything. No manual command needed.

### How it works

**Step 1 — Parse the spec**
Read `project_spec.md` to extract: domain/niche (e.g., DeFi, liquid staking, perp DEX), target audience, key product themes, and competitor names. Use this as a **relevance filter in Step 3**, not as a search limiter in Step 2.

**Step 2 — Run X trend searches**
Use web search to simulate real-time X monitoring. **Always start with broad crypto/Web3 market searches first**, then run spec-specific queries. Do NOT limit searches to the project's domain only — the goal is to surface the hottest topics across the entire market, then evaluate which ones are relevant.

Run all broad market searches first:
```
crypto twitter trending today
defi twitter hot topic this week
crypto CT discussion trending [current year]
altcoin narrative trending twitter [current year]
web3 viral tweet this week
crypto debate twitter [current year]
```

Then run spec-specific searches to find ecosystem angles:
```
site:x.com [domain keyword] -filter:replies
[domain keyword] trending twitter [current year]
[domain keyword] discussion OR debate OR thread twitter
[competitor name] twitter sentiment [current year]
```

**Step 3 — Score each topic by trending potential**

| Signal | Weight | Scoring |
|---|---|---|
| Recency (posted within 48h) | 30% | Within 24h = 10, 24–48h = 7, older = 3 |
| Estimated engagement | 30% | Viral (1K+ likes signals) = 10, high = 7, low = 3 |
| Content opportunity for spec audience | 25% | High fit (audience would search this) = 10, adjacent = 6, weak fit = 2 |
| Debate / controversy signal | 15% | Active debate = 10, one-sided = 5, none = 2 |

Note on "Content opportunity": a topic does NOT need to be about the spec's project directly. It just needs to be something the spec's target audience (e.g., DeFi users, crypto investors) would actively search for or care about. A trending narrative about Hyperliquid, Berachain, or ETH ETF is fair game even if the spec is Sonic-focused.

**Step 4 — Output trend alert**

Present at session start, before any user input:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔥 X TREND ALERT — [Date/Time]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Based on the full crypto/Web3 market scan, here's what's hot on X right now:

TREND 1 (Score: X/10) 🔴 HOT
  Topic:              [topic name]
  Why it's trending:  [1-sentence explanation]
  Audience fit:       [why your spec's audience would care about this]
  Blog angle:         [specific content angle]
  Suggested keyword:  "[keyword]"
  X discussion:       "[paraphrased post or thread summary]"

TREND 2 (Score: X/10) 🟡 RISING
  Topic:              [topic name]
  Why it's trending:  [1-sentence explanation]
  Audience fit:       [why your spec's audience would care about this]
  Blog angle:         [specific content angle]
  Suggested keyword:  "[keyword]"

TREND 3 (Score: X/10) 🟢 WATCH
  Topic:              [topic name]
  Why it's trending:  [1-sentence explanation]
  Audience fit:       [why your spec's audience would care about this]
  Blog angle:         [specific content angle]
  Suggested keyword:  "[keyword]"

→ Want to write about one of these? Say "go with Trend 1" and I'll start Stage 1 automatically.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### Limitations
- Simulated monitoring via web search — not a live X API connection.
- Results reflect what search engines have indexed from X, not live X data.
- If web search is disabled, skip Stage 0 and flag: "Stage 0 unavailable — web search is off. Please provide a keyword manually."

---

## Stage 1 — Keyword Research

### Goal
Identify 1 primary keyword + 5–10 secondary/LSI keywords with real data and scoring.

### Step 1 — Generate seed keywords
Brainstorm 8–12 candidates: head terms (1–2 words), mid-tail (3–4 words), long-tail / question variants (5+ words).

### Step 2 — Fetch Google Trends data
For each seed keyword, run:
- `google trends [keyword] 2025` → trend direction (rising / stable / declining)
- `[keyword] search interest 2025`

### Step 3 — Fetch X social buzz
For each seed keyword:
- `site:x.com [keyword]`
- `[keyword] trending twitter 2025`
- `[keyword] discussion reddit OR twitter OR forum`

### Step 4 — Fetch search volume signals
- `[keyword] search volume 2025`
- `ubersuggest [keyword]` or `semrush [keyword]` for visible free-tier data
- Google "People Also Ask" for [keyword] → extract as long-tail candidates
- Google "Related searches" for [keyword] → additional candidates

Label all estimated data as `[estimated]`.

Ask once: "Do you have an Ahrefs or SEMrush API key for exact volume data?" If yes, use it.

### Step 5 — Score and rank keywords

| Signal | Weight | Scoring |
|---|---|---|
| Search volume | 35% | <100=2, 100–1K=4, 1K–10K=7, 10K+=10 |
| Keyword difficulty (inverse) | 30% | Low=10, Medium=6, Hard=3 |
| Google Trends direction | 20% | Rising=9, Stable=6, Declining=2 |
| X/Social buzz | 15% | High=9, Medium=5, Low=2 |

Pick top 1 as primary, next 5–8 as secondary/LSI.

### Output format

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
Build a logically sequenced outline that follows the reader's mental journey, maps every long-tail keyword to a section, and flags UGC insertion points for Stage 3.

### Step 1 — Determine flow pattern

| Pattern | When to use | Arc |
|---|---|---|
| Problem → Solution | How-to, guides | Problem → Why → Solution → Validation |
| What → Why → How | Explainers | Definition → Importance → Application |
| Comparison | Best X, X vs Y | Context → Criteria → Options → Recommendation |
| Journey | Beginner guides | Starting point → Stages → End state |
| Argument | Opinion, trends | Claim → Evidence → Counter → Conclusion |

### Step 2 — Map long-tail keywords to sections
Assign each long-tail keyword to a specific H2 or H3. No section without a keyword anchor.

### Step 3 — Flag UGC insertion points
For each major H2, identify where community voice adds depth:
- Common misconceptions debated on X → add "Community Perspectives" H3
- Recurring user questions → convert to FAQ entry
- Real user experiences → flag for Stage 3 UGC mining

### Output format

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
  H3: 💬 UGC BLOCK — [community counterpoints]     ← Stage 3

H2: [Section 2]                                    🔑 [keyword]
  H3: [Subsection A]
  H3: 💬 UGC BLOCK — [real user experiences]       ← Stage 3

── FAQ ────────────────────────────────────
H2: Câu hỏi thường gặp
  H3: [Question 1]?
  H3: [Question 2]?                                💬 UGC source

── CONCLUSION ─────────────────────────────
  Summary: [2–3 key takeaways]
  Takeaway: [the one thing to remember]
  CTA: [specific next action]

KEYWORD COVERAGE CHECK:
  Primary keyword:    H1 ✓ | Intro ✓ | H2 ✓ | Conclusion ✓
  Long-tail keywords: [list each → assigned section ✓]
  Unplaced keywords:  [list → decide: add section or cut]
```

Ask: "Does this outline look good? Any changes before I draft?" — wait for confirmation before Stage 3/4.

---

## Stage 3 — UGC Enrichment

### Purpose
Mine real community comments from X threads, Reddit, and forums → transform them into ready-to-paste blog sections that add authentic human voice. This is the layer that separates this content from generic AI output — and the key signal that gets cited by AI search engines.

**Why this matters for GEO:** Reddit alone accounts for ~21% of citations in Google AI Overviews. Content with real UGC gets 2–3x more visibility than theory-only articles. E-E-A-T's "Experience" signal is the one thing AI-generated content fundamentally cannot fake.

### Trigger
Runs when `ugc_urls` are provided. If no URLs given, skip and note: "Stage 3 skipped — no UGC URLs provided."

### Step 1 — Fetch and extract comments
For each URL: use `web_fetch` to retrieve full page content. Extract: original post body, all comments with engagement metrics (likes, upvotes, reply count), timestamp, nesting level.
Fallback: if URL is behind a login wall → "Could not access [URL]. Paste comment text directly and I'll process it."

### Step 2 — Quality scoring (0–10)

| Signal | Weight | Scoring |
|---|---|---|
| Engagement (likes/upvotes) | 30% | Top 10% = 10, top 25% = 7, top 50% = 5, bottom 50% = 2 |
| Content length | 20% | <10 words = 1, 10–50 = 5, 50–150 = 8, 150+ = 10 |
| Contains data/numbers | 15% | Yes = 10, No = 3 |
| Personal experience markers | 15% | "I tried...", "In my case..." = 10, None = 3 |
| Substantive reply thread | 10% | 3+ quality replies = 10, 1–2 = 6, none = 3 |
| Sentiment strength | 10% | Strong opinion = 8, Neutral = 4 |

Filter: Score ≥6 → High Value. Score <3 → Discard (spam, memes, off-topic).

### Step 3 — Classify into 3 UGC categories

**Category A — Counter-Arguments:** challenges main article claims, edge cases, overlooked downsides.
Output: 150–300 word prose paragraph in Vietnamese, balanced tone.

**Category B — Real-World FAQs:** direct questions from comments, especially highly upvoted or repeated ones.
Output: Q&A pairs (3–6 max), answers in Vietnamese.

**Category C — Personal Experiences:** first-person accounts with specific numbers, before/after narratives.
Output: 2–4 mini case studies in Vietnamese, each 50–100 words, professionally paraphrased — never fabricated.

**Hard rules:** never fabricate comments or data points, never include real usernames (use "a user on X", "a Reddit commenter"), never include spam or personal attacks.

### Step 4 — Viral pattern analysis
For each high-value comment (score ≥7), identify why it resonated:

| Trigger | Description |
|---|---|
| Data-backed claim | Specific numbers, dollar amounts |
| Contrarian take | Opposes popular opinion with reasoning |
| Personal vulnerability | Shares failure or honest struggle |
| Insider knowledge | Suggests expertise or access |
| Simplification | Breaks down complexity clearly |

Output: top 3 viral triggers + 2 actionable writing tips.

### Step 5 — Map UGC blocks to outline
Match each UGC block to the insertion points flagged in the Stage 2 outline.

---

## Stage 4 — Draft Writing

### Goal
Write the full article following the outline, with UGC blocks inserted at flagged points. Human-style, data-backed, zero AI patterns — all in Vietnamese.

### Writing principles

**Structure:** Intro = Hook (specific stat/bold claim — never generic) → Problem → Promise. Body = follow outline exactly. UGC blocks at flagged points. Conclusion = synthesize key takeaways (do not restate all H2s) → clear CTA.

**Tone (default for crypto/Web3):** Expert-to-peer — assumes reader knows basic crypto, not a developer. Direct and confident, no hedging. Short sentences preferred; vary length for rhythm. Define technical terms inline on first use. Address the reader directly with "bạn".

**Data requirements:**
- Minimum 3 data points per article (stats, on-chain figures, market numbers).
- Source every stat inline: `[stat] (Source, Year)`.
- Find real stats via web search before drafting: `[topic] statistics 2025`, `[topic] data report 2025`.
- If no real data found: insert `[DATA NEEDED: search "[suggested query]"]` — never invent statistics.

**AI-pattern avoidance — never write:**
- "In today's fast-paced world" / "In the realm of"
- "It's important to note" / "It goes without saying"
- "Furthermore" / "Moreover" / "In conclusion"
- "Delve into" / "Dive into" / "Leverage" (abstract)
- "Game-changer" / "Revolutionary" / "Transformative" / "Comprehensive"
- "Have you ever wondered?"
- "Not only... but also"
- Vietnamese equivalents: "Trong thế giới ngày nay", "Điều quan trọng cần lưu ý là", "Hơn nữa" (repeated), "Tóm lại" (conclusion opener), "Chúng ta hãy cùng khám phá", "Mang tính cách mạng", "Toàn diện", "Bạn có bao giờ tự hỏi", "Không chỉ vậy mà còn"

**Keyword integration:**
- Primary keyword in first 100 words, at least one H2, and conclusion.
- Secondary/LSI keywords woven in naturally — never forced.
- Target density: 1–1.5% for primary keyword.

**Self-check before outputting the draft:**
1. Any "-" used as a list marker → replace with prose or numbered list.
2. Any "—" in body text → rewrite as two sentences.
3. Any banned AI phrase → rewrite with a specific fact.
4. Any H4/H5/H6 headings → convert to H3 or prose.
5. Any number written in full → convert to M/B/$M/$B format.

---

## Stage 4.5 — Visual & Link Enrichment

### Goal
Transform the raw draft into a visually credible, citation-verified document by: (1) generating data charts for key statistics, and (2) converting every source attribution into a live hyperlink.

Runs automatically after Stage 4 is complete. Cannot be skipped.

### Why this matters
Charts are 3x more likely to be cited by AI search engines than the same data in plain text. Inline hyperlinks signal editorial credibility to Google and AI crawlers. Every unlinked "— Source, Year" is a missed trust signal.

### Step 1 — Identify chart opportunities

A data point qualifies if it meets at least one of these criteria:

| Criterion | Example |
|---|---|
| Change over time (2+ periods) | "TVL grew from $2B to $8B in 6 months" |
| Compares 2+ assets or metrics | "Lido APY 3.8% vs solo staking 3.2%" |
| Inflow / outflow trend | "$1.2B ETF inflows in Q1 2025" |
| Index or score over time | "Fear & Greed Index: 12/100" |
| Ratio that changed | "ETH staking ratio: 18% → 27% in 12 months" |
| 3+ data points in a series | Monthly DEX volume figures |

**Chart types:**

| Data type | Chart type |
|---|---|
| Performance over time | Line chart with fill-under |
| Inflows / outflows | Bar chart — green positive, red negative |
| Index or score over time | Bar chart with color-coded zones |
| Ratio or comparison | Line or area chart |
| Single-point comparison | Horizontal bar or stat callout box |

**Chart design standards:**
- Background: `#F7F7F7`, no heavy gridlines.
- Primary color: `#E8650A` (adjust to project brand if spec defines one).
- Remove top and right spine.
- Annotate key data points directly on chart.
- Source line at bottom-left in gray italic.
- Font: DejaVu Sans. Resolution: 150 DPI minimum.
- Always generate alt text.
- Maximum 6 charts per article. Excess → stat callout boxes.

### Step 2 — Generate charts
Use Python + matplotlib. Execute in computing environment.

For each chart:
1. PNG image embedded in output.
2. Caption in Vietnamese: `Biểu đồ [N]: [what it shows]. [Time period]. Nguồn: [Name].`
3. Alt text (English OK for CMS): `[Chart type] showing [metric] from [start] to [end]. [Key finding].`

Place each chart immediately after the paragraph that first introduces its data. Never stack two charts back-to-back without body text between them.

### Step 3 — Convert citations to hyperlinks

Scan the draft for every inline source citation. Patterns to find:

| Pattern | Example |
|---|---|
| `(Nguồn, Năm)` | `(CoinDesk, tháng 1/2025)` |
| `theo [Nguồn]` | `theo DeFiLlama` |
| `[Nguồn] cho biết` | `Messari cho biết` |
| `[Nguồn] ghi nhận` | `Dune Analytics ghi nhận` |

For each citation:
1. Run web search: `[publication name] [topic] [approximate date]`.
2. Verify URL resolves.
3. Replace plain-text source with inline hyperlink, anchor text = source name.
4. If exact article not found: link to homepage + flag `[VERIFY URL]`.
5. If citation is vague: flag `[SOURCE NEEDED]` — never invent a source.

Link rules: prefer original publisher over aggregators. No paywalled links if a free version exists. Do not add links to unattributed claims.

### Step 4 — Output summary

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STAGE 4.5 — VISUAL & LINK ENRICHMENT SUMMARY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Charts generated:      [N] / [max 6]
  Chart 1: [title] → placed after [section name]
  Chart 2: [title] → placed after [section name]

Source links resolved: [N] / [total citations found]
  [Source name] → [URL] ✅
  [Source name] → [URL] ⚠️ [VERIFY URL — linked to homepage]

Unlinked citations flagged: [N]
  "[claim]" → [SOURCE NEEDED]

Alt text strings:
  Chart 1: "[alt text]"
  Chart 2: "[alt text]"
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Stage 5 — SEO + GEO Optimization

### SEO On-Page Checklist

- [ ] Meta title: 50–60 chars, primary keyword near the front.
- [ ] Meta description: 150–160 chars, primary keyword, includes hook/CTA.
- [ ] URL slug: short, lowercase, hyphenated, primary keyword.
- [ ] H1 contains primary keyword (only one H1).
- [ ] H2s use secondary keywords or question variants.
- [ ] Primary keyword in first 100 words and in conclusion.
- [ ] Keyword density: 1–1.5%.
- [ ] Paragraphs: max 3–4 lines.
- [ ] 2+ internal link suggestions (anchor text = secondary keywords).
- [ ] 1–2 authoritative external sources noted.
- [ ] Image alt text recommendations (min 2).
- [ ] FAQ → FAQPage schema; How-to steps → HowTo schema.

### GEO Rules (apply all 7)

GEO = Generative Engine Optimization. Goal: easy for Perplexity, Google SGE, ChatGPT Search to parse and cite.

1. **Answer-first every H2** — 1–2 sentence direct answer before elaboration.
2. **Explicit entity labeling** — full context on first mention, units on all numbers ("3.2% APY"), explicit dates ("tính đến Q1 2025").
3. **FAQ mandatory (min 5)** — each answer self-contained, 50–150 words, direct answer first.
4. **Featured snippet block** — 40–60 words, placed within first H2, paragraph OR numbered list (not mixed).
5. **Citation-friendly** — each factual claim on its own sentence, data formatted consistently, no pronoun ambiguity.
6. **Secondary keywords in internal link anchor text.**
7. **UGC sections present** — confirms E-E-A-T "Experience" signal.

**GEO Output Block (add to QA Report):**

```
GEO OPTIMIZATION CHECKLIST
Answer-first structure (each H2):   ✅/❌
Explicit entity labeling:           ✅/❌
FAQ section (min 5 Q&A):            ✅/❌
Featured snippet candidate block:   ✅/❌ [paste block here]
Citation-friendly formatting:       ✅/❌
Suggested structured data:
  FAQPage schema:                   ✅ applicable
  Article schema:                   ✅ applicable
  HowTo schema:                     ✅/❌ [applicable if how-to steps present]
UGC sections (E-E-A-T):            ✅/❌ [X sections from Stage 3]
AI-bot parse score:                 [X/10]
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

Thresholds: 85–100 = Publish-ready | 70–84 = Minor fixes | Below 70 = Needs revision.

### Full Report Output

```
╔══════════════════════════════════════════════╗
║       CONTENT PIPELINE PRO — QA REPORT       ║
╚══════════════════════════════════════════════╝

ARTICLE: [Title]
KEYWORD: [Primary keyword]
WORD COUNT: [X words]
UGC SECTIONS: [X sections from Stage 3]

SEO SCORE: [X/100]

| Check                                | Points | Status | Details |
|--------------------------------------|--------|--------|---------|
| Primary keyword in meta title        | 10     | ✅/❌  | [details] |
| Primary keyword in H1                | 10     | ✅/❌  | [details] |
| Primary keyword in first 100 words   | 10     | ✅/❌  | [details] |
| Keyword density (1–1.5%)             | 15     | ✅/❌  | [X%] |
| Meta title length (≤60 chars)        | 10     | ✅/❌  | [X chars] |
| Meta description length (≤160 chars) | 10     | ✅/❌  | [X chars] |
| H2/H3 structure                      | 10     | ✅/❌  | [details] |
| Image alt text suggestions           | 5      | ✅/❌  | [details] |
| Internal linking                     | 10     | ✅/❌  | [details] |
| Readability                          | 10     | ✅/❌  | [details] |

GEO SCORE: [X/10]
[GEO checklist block from Stage 5]

WRITING RULES CHECK
"-" symbol used as list marker:      [count] / target: 0
"—" em dash in body text:            [count] / target: 0
Number format (M/B/$M/$B):           ✅/❌ [errors if any]
Sentence capitalization:             ✅/❌
Sentence-ending punctuation:         ✅/❌
Logical sentence flow:               ✅/❌ [sections with issues if any]
AI patterns detected:                [count] [location]
Heading structure (H1/H2/H3 only):   ✅/❌

WRITING QUALITY
AI patterns detected: [count] [list with location]
Tone consistency: [Consistent / Flags: section X drifts]
Fact-check flags: [claims marked [VERIFY]]
Data points: [X] — [meets / below minimum of 3]

FINAL VERDICT
SEO:     [Publish-ready / Minor fixes / Needs revision]
GEO:     [Strong / Needs improvement]
UGC:     [Enriched / Missing — add Stage 3 URLs]
Verdict: [Publish-ready / Minor fixes / Needs revision]

Actions before publishing:
1. [Action 1]
2. [Action 2]
```

---

## Edge Cases

| Case | Action |
|---|---|
| Keyword too broad (e.g. "crypto") | Stop. Suggest 3–5 long-tail alternatives. Ask user to choose before continuing. |
| Spec file missing info | Use defaults. Flag every assumption with `[ASSUMED]`. |
| Keyword doesn't match spec | Warn about mismatch. Ask for confirmation before continuing. |
| Deep technical content | Flag sections with `[SME REVIEW]`. Never fabricate technical details. |
| Word count <500 or >5000 | Warn. Recommend 800–2,500 for this topic type. |
| SEO score below 70 | Mark "Needs revision". List specific fixes with section references. |
| Web search unavailable | Flag each stage that requires it. Skip Stage 0. Fall back to training knowledge, label `[estimated]`. |
| UGC URL behind login wall | Skip URL. Request user to paste comment text directly. |
| No high-value comments (all score <3) | Return: "No high-value comments in this thread. Try a different URL with more substantive discussion." |
| <10 comments total | Process all. Add warning: "Limited comment data — insights may not be representative." |
| Stage 0 finds no trending topics | Return 3 evergreen topics from spec context. |
| Stage 4.5: no chart-worthy data | Output stat callout boxes for all key numbers. Flag: "No time-series or comparison data found — consider adding benchmark data in Stage 4 revision." |
| Stage 4.5: all source URLs paywalled | Link to publisher homepages. Flag every instance `[VERIFY URL]`. List all in enrichment summary. |

---

## Limitations

- Stage 0 is simulated monitoring via web search — not a live X API connection.
- Keyword volume data is estimated unless user provides API key.
- Does not connect to SEMrush/Ahrefs APIs automatically.
- Does not publish to any CMS.
- Generates charts from in-draft data (matplotlib); does NOT generate decorative/editorial images.
- `[VERIFY]`, `[DATA NEEDED]`, `[SOURCE NEEDED]`, and `[VERIFY URL]` flags require human review before publishing.
- SEO/GEO scores are based on internal rubric, not third-party tools.
- UGC covers publicly accessible pages only.

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
| Source hyperlinking | Inconsistent / skipped | 100% of citations linked | 100% coverage |
| Scale capacity | 1–2 articles/day | 8–10 articles/day | 5x |

---

## Expansion Roadmap

- Real X API integration: replace simulated monitoring with live streaming API.
- Ahrefs/SEMrush API: exact keyword volume data instead of estimates.
- Auto-generate featured images via AI image generation (separate from Stage 4.5 data charts).
- Multi-format output: one blog → Twitter thread, LinkedIn post, Telegram post, newsletter.
- Content Calendar: input 10 keywords → full monthly content calendar.
- Performance tracking: monitor ranking + traffic post-publish → feed back to refine skill.
- Batch mode: 10 keywords → 10 blogs + 10 QA reports.

---

## Tech Stack

- **Primary:** Claude Project (or Custom GPT).
- **Skill format:** `SKILL.md` with structured instructions.
- **Web search:** enabled — required for Stage 0, Stage 1, Stage 4 data sourcing, Stage 4.5 link resolution.
- **URL fetching:** `web_fetch` — required for Stage 3 UGC mining and Stage 4.5 URL verification.
- **Chart generation:** Python + matplotlib — required for Stage 4.5 visual enrichment.
- **Input format:** `.md` file (spec) + text input (keyword/topic) + optional URLs (UGC).
- **Output format:** `.docx` (full article with embedded charts + hyperlinks) + `.md` (brief, QA report).
