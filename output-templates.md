# Output Templates — Content Pipeline Pro

Standard output formats for each stage. Copy these into AI output exactly.

---

## Stage 0 — Trend Alert

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔥 X TREND ALERT — [Today's Date]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Based on your project spec, here's what's hot on X right now:

TREND 1 (Score: X/10) 🔴 HOT
  Topic:             [topic name]
  Why it's trending: [1-sentence explanation]
  Blog angle:        [specific content angle]
  Suggested keyword: "[keyword]"
  X discussion:      "[paraphrased thread summary]"

TREND 2 (Score: X/10) 🟡 RISING
  Topic:             [topic name]
  Why it's trending: [1-sentence explanation]
  Blog angle:        [specific content angle]
  Suggested keyword: "[keyword]"

TREND 3 (Score: X/10) 🟢 WATCH
  Topic:             [topic name]
  Why it's trending: [1-sentence explanation]
  Blog angle:        [specific content angle]
  Suggested keyword: "[keyword]"

→ Say "go with Trend 1" and I'll run the full pipeline.
→ Or give me your own keyword and I'll start from Stage 1.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Stage 1 — Keyword Research Results

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
KEYWORD RESEARCH RESULTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

PRIMARY KEYWORD (Score: X/10)
  Keyword:       [keyword]
  Volume:        [X/month — estimated]
  Difficulty:    [Low / Medium / Hard]
  Trend:         [Rising📈 / Stable➡️ / Declining📉]
  X Buzz:        [High/Medium/Low] — "[what people debate on X]"
  Search Intent: [Informational / Navigational / Transactional / Commercial]

SECONDARY KEYWORDS:
┌─────────────────────────┬────────┬──────┬────────────┬──────────┬───────┐
│ Keyword                 │ Volume │  KD  │ Trend      │ Buzz     │ Score │
├─────────────────────────┼────────┼──────┼────────────┼──────────┼───────┤
│ [keyword 1]             │ [est.] │ [KD] │ Rising📈   │ High     │  X.X  │
│ [keyword 2]             │ [est.] │ [KD] │ Stable➡️   │ Medium   │  X.X  │
│ [keyword 3]             │ [est.] │ [KD] │ Declining📉│ Low      │  X.X  │
└─────────────────────────┴────────┴──────┴────────────┴──────────┴───────┘

KEY INSIGHT FROM SOCIAL DATA:
"[what people are actually debating on X/forums]"
→ Use this as the hook in intro and FAQ.

CONTENT ANGLE:
[1–2 sentences — unique angle based on trending signals + content gap found]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Stage 2 — Content Brief

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CONTENT BRIEF
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Target Keyword:     [primary keyword]
Flow Pattern:       [Problem→Solution / What→Why→How / Comparison / Journey / Argument]
Search Intent:      [type]
Recommended Length: [X words]
Target Audience:    [who, what they know, what they need]
GEO Target:         Perplexity / Google SGE / ChatGPT Search

LONG-TAIL KEYWORD MAP:
  [keyword 1] → H2: [section title]
  [keyword 2] → H3: [subsection title]
  [keyword 3] → FAQ: [question form]

UGC INSERTION POINTS:
  [Section X] ← UGC: community counterpoints
  [Section Y] ← UGC: real user experiences
  [FAQ]       ← UGC: real questions from X/Reddit

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
OUTLINE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

H1: [Title — primary keyword + compelling angle]

── INTRO ─────────────────────────────
  Hook:    [specific stat or bold claim]
  Problem: [what the reader struggles with]
  Promise: [what this article delivers]
  [Featured snippet block — 40–60 words]

── BODY ──────────────────────────────
H2: [Section 1]                                    🔑 [keyword]
  H3: [Subsection A]
  H3: [Subsection B]
  H3: 💬 UGC BLOCK — community counterpoints       ← Stage 3

H2: [Section 2]                                    🔑 [keyword]
  H3: [Subsection A]
  H3: 💬 UGC BLOCK — real user experiences         ← Stage 3

[... continue for all mapped keywords ...]

── FAQ ───────────────────────────────
H2: Frequently Asked Questions   (min 5 — mandatory for GEO)
  H3: [Question]?                                  🔑 [keyword]
  H3: [Question]?                                  💬 UGC source
  H3: [Question]?                                  🔑 [keyword]
  H3: [Question]?                                  💬 UGC source
  H3: [Question]?                                  🔑 [keyword]

── CONCLUSION ────────────────────────
  Summary:  [2–3 key takeaways — synthesize, don't restate H2s]
  Takeaway: [the one thing to remember]
  CTA:      [specific next action]

KEYWORD COVERAGE CHECK:
  Primary keyword:    H1 ✓ | Intro ✓ | min 1 H2 ✓ | Conclusion ✓
  Long-tail keywords: [list each → assigned section ✓]
  Unplaced keywords:  [list any → decide: add section or cut]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Stage 3 — UGC Enrichment Report

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
UGC ENRICHMENT REPORT
Sources: [X] URLs | Total comments: [X] | High-value: [Y] ([Z]%)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SECTION A: COMMUNITY PERSPECTIVES — NOTABLE COUNTERPOINTS
[150–300 word balanced prose — ready to copy-paste into blog]
→ INSERT AFTER: [H2 section name from outline]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SECTION B: FAQ — REAL QUESTIONS FROM THE COMMUNITY
Q1: [Real question — paraphrased for clarity]
A1: [Synthesized answer from community + knowledge]
    Source: [X] users asked this | Top answer: [Y] upvotes
→ INSERT INTO: FAQ section

[... up to Q6 maximum ...]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SECTION C: REAL USER EXPERIENCES
CASE 1: [Descriptive title]
[Paraphrased experience — professional tone, original details preserved. Never fabricated.]
— Source: [Platform] user | [X] likes/upvotes
— Viral trigger: [data-backed claim / contrarian take / personal vulnerability / insider knowledge / simplification / prediction]
→ INSERT AFTER: [H2 section name from outline]

[... up to CASE 4 maximum ...]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

VIRAL PATTERN ANALYSIS
Top triggers:
  1. [Trigger type]: [X] comments — "[paraphrased example]"
  2. [Trigger type]: [X] comments — "[paraphrased example]"
  3. [Trigger type]: [X] comments — "[paraphrased example]"

Writing tips for your draft:
  → [Tip 1 based on dominant pattern]
  → [Tip 2]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Stage 4 — Blog Article

```md
# [Article H1 Title]

**Meta Title**: [≤60 chars — primary keyword near front]
**Meta Description**: [≤160 chars — primary keyword + hook]

---

[Full article body]
[H2/H3 structure following outline]
[UGC blocks at flagged insertion points]
[Min 3 data points, each formatted: stat — Source, Year]
[Featured snippet block within first H2: 40–60 words, direct definition or numbered steps]

---

**Internal Linking Suggestions:**
- "[anchor text using secondary keyword]" → [destination page] — place in [section name]
- "[anchor text using secondary keyword]" → [destination page] — place in [section name]
```

---

## Stage 5 — GEO Checklist Block

```
GEO OPTIMIZATION CHECKLIST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Answer-first structure (each H2):    ✅/❌
Explicit entity labeling:            ✅/❌
FAQ section present (min 5 Q&A):     ✅/❌
Featured snippet candidate block:    ✅/❌
  [paste the 40–60 word block here]
Citation-friendly formatting:        ✅/❌
Internal links use secondary KWs:    ✅/❌
UGC sections present (E-E-A-T):      ✅/❌ — [X sections from Stage 3]

Structured data suggestions:
  FAQPage schema:   ✅ → apply to FAQ section
  Article schema:   ✅ → apply to full post (datePublished, author, headline)
  HowTo schema:     ✅/❌ → if how-to steps present
  BreadcrumbList:   ✅ → for site navigation

GEO Score: [X/10]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Stage 6 — QA Report

```
╔══════════════════════════════════════════════╗
║       CONTENT PIPELINE PRO — QA REPORT       ║
╚══════════════════════════════════════════════╝
ARTICLE: [Title] | KEYWORD: [primary] | WORDS: [X] | UGC: [X sections / None]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SEO SCORE: [X/100]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
| Check                                  | Points | Status | Details |
|----------------------------------------|--------|--------|---------|
| Primary keyword in meta title          |   10   | ✅/❌  | [notes] |
| Primary keyword in H1                  |   10   | ✅/❌  | [notes] |
| Primary keyword in first 100 words     |   10   | ✅/❌  | [notes] |
| Keyword density (1–1.5%)               |   15   | ✅/❌  | [X%]    |
| Meta title ≤60 chars                   |   10   | ✅/❌  | [X chars]|
| Meta description ≤160 chars            |   10   | ✅/❌  | [X chars]|
| H2/H3 structure (min 3 H2s)            |   10   | ✅/❌  | [notes] |
| Image alt text suggestions (min 2)     |    5   | ✅/❌  | [notes] |
| Internal linking suggestions (min 2)   |   10   | ✅/❌  | [notes] |
| Readability (paragraphs ≤4 lines)      |   10   | ✅/❌  | [notes] |

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
GEO SCORE: [X/10]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[GEO checklist block from Stage 5]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
WRITING QUALITY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
AI patterns detected: [count] — [list each with location]
Tone consistency:     [Consistent / Flags: section X drifts]
Data points:          [X found] — [meets / below minimum of 3]
Fact-check flags:     [list all [VERIFY] and [DATA NEEDED] markers]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
FINAL VERDICT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SEO:     [Publish-ready / Minor fixes / Needs revision]
GEO:     [Strong / Needs improvement / Weak]
UGC:     [Enriched / Missing — provide ugc_urls to enrich]
VERDICT: [Publish-ready / Minor fixes / Needs revision]

Key actions before publish:
1. [Specific action — section reference]
2. [Specific action — section reference]
```
