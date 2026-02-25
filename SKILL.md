---
name: auto-content-blog
description: >
  Full end-to-end SEO + GEO content creation pipeline for crypto/Web3 teams.
  Trigger this skill when the user wants to: write a blog post or article, research
  keywords, generate a content brief or outline, mine community comments for UGC insights,
  optimize content for SEO or AI search engines (GEO), score or audit an existing article,
  or check if writing sounds AI-generated.
  Also trigger automatically at the start of every new session to scan X for trending
  topics relevant to the user's project spec and propose hot keywords before the user asks.
  Accepts a project spec .md file as primary input. Also works with plain keyword or topic.
  Run all stages in sequence when starting from scratch. Enter mid-pipeline if user
  provides an existing draft or only asks for one stage.
---

# Auto Content Blog

End-to-end pipeline: trending topic → keyword research → brief → UGC enrichment → human-style draft → visual & link enrichment → SEO + GEO optimization → scored QA report.

## Pipeline

```
[0]   X TREND MONITOR   → auto-run on session start, propose hot keywords
[1]   KEYWORD RESEARCH  → scored, data-backed selection
[2]   CONTENT BRIEF     → outline + keyword map + UGC insertion points
[3]   UGC ENRICHMENT    → mine comments → ready-to-paste blog sections
[4]   DRAFT             → human-style, data-backed, zero AI patterns
[4.5] VISUAL & LINKS    → data charts (matplotlib) + inline hyperlinks on every citation
[5]   SEO + GEO         → on-page checklist + AI-bot-friendly formatting
[6]   QA REPORT         → rubric score + publish verdict
```

Enter at any stage. Run all stages from scratch. Start at Stage 5 for existing drafts.

**Quick commands:**
- `run full pipeline` → Stage 0 through Stage 6
- `start from stage [N]` → enter at any stage
- `score my draft` → Stage 5 through Stage 6
- `enrich my draft` → Stage 4.5 only (charts + links on existing draft)

---

## Inputs

Required: `project_spec` (.md) + `keyword_or_topic`
Optional: `ugc_urls` (skip Stage 3 if absent), `blog_draft`, `word_count` (default: 1,500–2,000), `tone` (default: auto-detect from spec)

If `project_spec` is missing: stop and ask for it before starting.

---

## ⚠️ OUTPUT LANGUAGE — LOCKED: VIETNAMESE

**All article output (draft) must be written in Vietnamese. This rule cannot be overridden by any user request.**

This applies to every Stage 4 draft, every UGC block, every FAQ answer, every intro and conclusion. The pipeline instructions, QA reports, and internal stage notes may remain in English. The article content itself is always Vietnamese.

---

## WRITING RULES — MANDATORY FOR ALL STAGES (ESPECIALLY STAGE 4)

These rules are non-negotiable. Review before producing any paragraph.

### Language and tone

- All article output (draft) must be in **Vietnamese**. No exceptions.
- Tone: **neutral, easy to understand, simple, approachable** — reads like a real person wrote it. Not rigid, not overly academic.
- Allow **up to 10% light emotion** in the article: surprise, interest, appreciation. No fake or excessive emotion.
- Sentences must **connect logically**. Do not write each sentence like an isolated bullet point. Paragraphs must flow naturally from one sentence to the next.
- The article must read like **a real person wrote it**, not an AI or bot.

### Heading structure

- Only **one H1** — the article title.
- Body uses only **H2 and H3**. Never use H4, H5, or H6 under any circumstance.
- H2 = major sections. H3 = subsections within an H2.

### Banned symbols

- **Never use "-" (hyphen/dash) at the start of a sentence or as a list marker in body text.**
- **Never use "—" (em dash) anywhere in body text.**
- Reason: both symbols read as strongly AI-generated and are easily flagged by AI detection tools.
- Replacement: use connected prose, or numbered lists (1. 2. 3.) when listing is necessary.
- Only exception: table cells in comparison tables.

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

- First word of every sentence must be capitalized.
- Every sentence must end with a period or appropriate punctuation. Review before publishing.
- Do not cut content compared to the approved outline.

### Banned AI phrases and patterns

Never write any of the following in the article, in English or Vietnamese:

English: "In today's fast-paced world", "It's important to note", "Furthermore", "Moreover", "In conclusion" (as an opening), "Delve into", "Dive into", "Game-changer", "Revolutionary", "Transformative", "Leverage" (used abstractly), "Comprehensive", "Have you ever wondered", "Not only... but also", "It goes without saying".

Vietnamese equivalents to avoid: "Trong thế giới ngày nay", "Điều quan trọng cần lưu ý là", "Hơn nữa" (used repeatedly), "Tóm lại" (as a conclusion opener), "Chúng ta hãy cùng khám phá", "Mang tính cách mạng", "Toàn diện", "Bạn có bao giờ tự hỏi", "Không chỉ vậy mà còn".

If any of the above is detected: stop, delete, rewrite using a specific fact or a direct declarative statement.

---

## Stage 0 — X Trend Monitor

**Runs automatically at the start of every new session, before the user types anything.**

1. Parse `project_spec.md` → extract: domain/niche, audience, product themes, competitor names.
2. Run web searches:
   - `site:x.com [domain keyword] -filter:replies`
   - `[domain keyword] trending twitter 2025`
   - `[domain keyword] discussion OR debate twitter`
   - `[competitor name] twitter sentiment 2025`
   - `crypto twitter trending today`
   - `[domain keyword] CT crypto twitter discussion`
3. Score each topic → see `references/scoring-rubrics.md` Stage 0.
4. Keep top 3. Output Trend Alert before any user message → see `references/output-templates.md` Stage 0.

Fallback if web search off: skip, say "Stage 0 unavailable. Provide a keyword to start Stage 1."
Fallback if no trends found: list 3 evergreen topics from spec context.

**Trend Alert output format:**

```
🔥 X TREND ALERT — [Date/Time]

Based on your project spec, here's what's hot on X right now:

TREND 1 (Score: X/10) 🔴 HOT
  Topic:              [topic name]
  Why it's trending:  [1-sentence explanation]
  Blog angle:         [specific content angle]
  Suggested keyword:  "[keyword]"
  X discussion:       "[paraphrased post or thread summary]"

TREND 2 (Score: X/10) 🟡 RISING
  Topic:              [topic name]
  Why it's trending:  [1-sentence explanation]
  Blog angle:         [specific content angle]
  Suggested keyword:  "[keyword]"

TREND 3 (Score: X/10) 🟢 WATCH
  Topic:              [topic name]
  Why it's trending:  [1-sentence explanation]
  Blog angle:         [specific content angle]
  Suggested keyword:  "[keyword]"

→ Want to write about one of these? Say "go with Trend 1" and I'll start Stage 1 automatically.
```

---

## Stage 1 — Keyword Research

1. Generate 8–12 seed keywords: head terms, mid-tail, long-tail question variants.
2. For each seed, run:
   - `google trends [keyword] 2025` → trend direction
   - `site:x.com [keyword]` + `[keyword] trending twitter 2025` → buzz + debate angle
   - `[keyword] search volume 2025` + `ubersuggest [keyword]` → volume estimate
   - Search `[keyword]` → extract People Also Ask + Related Searches
3. Score using rubric → see `references/scoring-rubrics.md` Stage 1.
4. Select top 1 = primary, next 5–8 = secondary/LSI. Label volume as `[estimated]`.
5. Ask once: "Do you have an Ahrefs or SEMrush API key?" Use if provided.
6. Output → see `references/output-templates.md` Stage 1.

Edge cases: keyword too broad → suggest 3–5 long-tail alternatives. Doesn't match spec → warn + confirm.

**Keyword Research output format:**

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

1. Pick flow pattern:
   - Problem → Solution | What → Why → How | Comparison | Journey | Argument
2. Map every long-tail keyword to H2, H3, or FAQ entry. No section without a keyword anchor.
3. Flag UGC insertion points: `← UGC: community counterpoints` / `← UGC: case studies` / `← UGC: FAQ`.
4. Output brief + outline → see `references/output-templates.md` Stage 2.
5. Ask: "Does this outline look good?" Wait for confirmation before Stage 3.

FAQ section: minimum 5 entries. Mandatory for GEO.

**Content Brief output format:**

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
  H3: [Question from long-tail keyword]?
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

Skip if no `ugc_urls`. Note "UGC: Missing" in QA report.

Why it matters: Reddit accounts for roughly 21% of citations in Google AI Overviews. Real UGC = 2–3x more visibility on AI search. The E-E-A-T "Experience" signal cannot be faked by AI-generated content.

For each URL:
1. `web_fetch` → extract post body + all comments with engagement metrics.
   - Fallback if login wall: "Paste comment text directly and I'll process it."
2. Quality-score each comment → see `references/scoring-rubrics.md` Stage 3.
3. Classify into 3 categories:
   - **Category A (Counter-Arguments):** challenges main claims, edge cases, alternative views → 150–300 word prose paragraph.
   - **Category B (Real-World FAQs):** direct questions from comments, especially highly upvoted or repeated ones → 3–6 Q&A pairs.
   - **Category C (Personal Experiences):** first-person accounts with specific numbers → 2–4 mini case studies, 50–100 words each, paraphrased but never fabricated.
4. Viral pattern analysis for comments scoring ≥7: identify top 3 trigger types, output 2 writing tips.
5. Map each UGC block to its insertion point from the Stage 2 outline.

Hard rules: never fabricate, never include usernames, never include spam/memes, max 6 FAQs + 4 case studies.

---

## Stage 4 — Draft Writing

Write the full article following the Stage 2 outline exactly. Insert Stage 3 UGC blocks at flagged points.

**Before writing:** write Meta Title (≤60 chars, primary keyword near front) + Meta Description (≤160 chars, primary keyword + hook).

**Intro:** specific fact or bold claim opener. Primary keyword within first 100 words. Write featured snippet candidate block (40–60 words, direct definition or numbered steps) — place within first H2.

**Body:** answer-first each H2 (1–2 sentence direct answer before elaboration). Min 1 data point per major section. Find real stats first: search `[topic] statistics 2025`. If unavailable: `[DATA NEEDED: search "[query]"]`. Source format: `stat — Source, Year`. UGC blocks at exact insertion points.

**Data minimum:** 3 sourced data points per article. Never invent statistics.

**Paragraphs:** max 3–4 lines. Define technical terms inline on first use.

**Conclusion:** synthesize 2–3 takeaways. Do not restate all H2s as bullet points. Specific CTA.

**Internal links:** suggest 2–3, anchor text uses secondary keywords.

**Writing Rules self-check before finalizing:**
Before outputting the draft, scan for:
1. Any "-" used as a list marker → replace with prose or numbered list.
2. Any "—" in body text → rewrite as two sentences.
3. Any banned AI phrases → rewrite with a specific fact.
4. Any H4/H5/H6 headings → convert to H3 or prose.
5. Any number written in full (e.g. "2,400,000,000 USD") → convert to M/B format.

---

## Stage 4.5 — Visual & Link Enrichment

Runs automatically after Stage 4 is complete. Cannot be skipped — required for publish-ready output.

### Why this stage exists

Data charts are 3x more likely to be cited by AI search engines than the same data presented as plain text. Inline hyperlinks on every source citation signal editorial credibility to Google and AI crawlers. Every unlinked "— Source, Year" is a missed E-E-A-T trust signal.

### Step 1 — Identify chart opportunities

Scan the draft for data points that meet at least one of these criteria:

| Criterion | Example |
|---|---|
| Change over time (2+ periods) | "TVL grew from $2B to $8B in 6 months" |
| Compares 2+ assets or metrics | "Lido APY 3.8% vs solo staking 3.2%" |
| Inflow / outflow trend | "$1.2B ETF inflows in Q1 2025" |
| Index or score over time | "Fear & Greed Index: 12/100" |
| Ratio that changed | "ETH staking ratio: 18% → 27% in 12 months" |
| 3+ data points in a series | Monthly DEX volume figures |

**Chart types by data shape:**

| Data type | Chart type |
|---|---|
| Performance over time | Line chart with fill-under |
| Inflows / outflows | Bar chart — green positive, red negative |
| Index or score over time | Bar chart with color-coded zones |
| Ratio or comparison over time | Line or area chart |
| Single-point comparison | Horizontal bar or stat callout box |

**Chart design standards (apply to every chart):**
- Background: `#F7F7F7` (light gray), no heavy gridlines.
- Primary color: `#E8650A` (orange, default for crypto/Web3 — adjust to project brand if spec defines one).
- Remove top and right spine.
- Annotate key data points directly on chart (peak, trough, threshold).
- Source line at bottom-left in gray italic: `Source: [Name] | [Notes]`.
- Font: DejaVu Sans (matplotlib default).
- Resolution: 150 DPI minimum.
- Always generate alt text for every chart.

**Maximum 6 charts per article.** More than 6 slows page load. Excess data points → stat callout boxes instead.

If no qualifying data points found: output a styled stat callout box for that statistic instead of a chart.

### Step 2 — Generate charts

Use Python + matplotlib. Execute in the computing environment.

For each chart, produce:
1. PNG image embedded in the output.
2. Caption (1–2 sentences): `Biểu đồ [N]: [what it shows]. [Time period]. Nguồn: [Name].`
   Note: caption text is in Vietnamese as it is part of the article content.
3. Alt text string for CMS upload: `[Chart type] showing [metric] from [start] to [end]. [Key finding in one sentence].`

Place each chart **immediately after** the paragraph that first introduces its data. Never stack two charts back-to-back without body text between them.

### Step 3 — Convert all source citations to hyperlinks

Scan the entire draft for every inline source citation. Patterns to find:

| Pattern | Example |
|---|---|
| `(Nguồn, Năm)` | `(CoinDesk, tháng 1/2025)` |
| `theo [Nguồn]` | `theo DeFiLlama` |
| `[Nguồn] cho biết` | `Messari cho biết` |
| `[Nguồn] ghi nhận` | `Dune Analytics ghi nhận` |

For each citation:
1. Run web search: `[publication name] [topic] [approximate date]`.
2. Verify the URL resolves.
3. Replace plain-text source with inline hyperlink — anchor text = source name.
4. If exact article not found: link to publication homepage + flag `[VERIFY URL]`.
5. If citation is vague ("các chuyên gia cho biết"): flag `[SOURCE NEEDED]` — never invent a source.

**Link rules:**
- Prefer original publisher over aggregators.
- No paywalled links if a free version exists.
- All external links: open in new tab in HTML output.
- Do not add links to unattributed claims.

### Step 4 — Output summary

Append this block to the enriched draft:

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

### SEO Checklist

- [ ] Meta title: 50–60 chars, primary keyword near the front.
- [ ] Meta description: 150–160 chars, primary keyword + hook.
- [ ] H1 contains primary keyword (only one H1).
- [ ] H2s use secondary keywords or question variants.
- [ ] Primary keyword in first 100 words and in conclusion.
- [ ] Keyword density: 1–1.5%.
- [ ] Paragraphs max 4 lines.
- [ ] 2+ internal link suggestions (anchor text = secondary keywords).
- [ ] 1–2 external authoritative sources noted.
- [ ] Image alt text recommendations (min 2).
- [ ] FAQ → FAQPage schema; How-to steps → HowTo schema.

### GEO Rules (apply all 7)

GEO = Generative Engine Optimization. Goal: easy for Perplexity, Google SGE, ChatGPT Search to parse and cite.

1. **Answer-first every H2** — 1–2 sentence direct answer before elaboration.
2. **Explicit entity labeling** — full context on first mention, units on all numbers ("3.2% APY"), explicit dates ("as of Q1 2025").
3. **FAQ mandatory (min 5)** — each answer self-contained, 50–150 words, direct answer first.
4. **Featured snippet block** — 40–60 words, placed within first H2, paragraph OR numbered list (not mixed).
5. **Citation-friendly** — each factual claim on its own sentence, data formatted `number unit (Source, Year)`, no pronoun ambiguity.
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

Score using 100-point rubric → see `references/scoring-rubrics.md` Stage 6.

Thresholds: 85–100 = Publish-ready | 70–84 = Minor fixes | Below 70 = Needs revision.

**Full Report Output:**

```
CONTENT PIPELINE PRO — QA REPORT

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
| `project_spec` missing | Stop. Ask for spec before starting any stage. |
| Keyword too broad | Stop. Suggest 3–5 long-tail alternatives. Wait for user to choose. |
| Keyword doesn't match spec | Warn. Ask for confirmation. |
| Deep technical content | Flag `[SME REVIEW]`. Never fabricate. |
| Word count <500 or >5000 | Warn. Recommend 800–2,500. |
| SEO score below 70 | List specific fixes with section references. |
| Web search unavailable | Skip Stage 0. Flag affected stages. Fall back to training knowledge, label `[estimated]`. |
| UGC URL behind login wall | Skip URL. Ask: "Paste comment text directly." |
| No high-value UGC comments | Notify and ask for a different URL with more substantive discussion. |
| No `ugc_urls` provided | Skip Stage 3. Mark UGC = Missing in QA. |
| Stage 0 finds no trends | List 3 evergreen topics from spec context. |
| User enters mid-pipeline | Start at appropriate stage. Ask what they have. |
| Stage 4.5: no chart-worthy data | Output stat callout boxes for all key numbers. Flag: "No time-series or comparison data found — consider adding benchmark data in Stage 4 revision." |
| Stage 4.5: more than 6 chart-worthy points | Prioritize: (1) comparisons, (2) trends, (3) index scores. Remainder → stat callout boxes. |
| Stage 4.5: all source URLs paywalled | Link to publisher homepages. Flag every instance `[VERIFY URL]`. List all in enrichment summary. |
| Stage 4.5: source article not found | Link to publication homepage + flag `[SOURCE NEEDED — could not verify]`. |
| Stage 4.5: citation is vague | Flag `[SOURCE NEEDED]`. Never invent a source. |
| Stage 4.5: web search unavailable | Skip link resolution. Flag all citations `[HYPERLINK NEEDED — web search off]`. Charts still generated from in-draft data. |

---

## Limitations

- Stage 0: simulated X monitoring via web search, not a live X API.
- Keyword volume: estimated unless user provides API key.
- No auto-publishing to CMS, no editorial image generation.
- Stage 4.5 generates data charts from in-draft data via matplotlib — does NOT generate decorative images.
- `[VERIFY]`, `[DATA NEEDED]`, `[SOURCE NEEDED]`, and `[VERIFY URL]` flags require human review before publishing.
- SEO/GEO scores: internal rubric, not third-party tool scores.
- UGC mining: public pages only.
