---
name: content-pipeline-pro
description: >
  Full end-to-end SEO + GEO content creation pipeline for crypto/Web3 teams.
  Trigger this skill when the user wants to: write a blog post or article, research
  keywords, generate a content brief or outline, mine community comments for UGC insights,
  optimize content for SEO or AI search engines (GEO), score or audit an existing article,
  or check if writing sounds AI-generated.
  Also trigger automatically at the start of every new session to scan X for trending
  topics relevant to the user's project spec — propose hot keywords before the user asks.
  Accepts a project spec .md file as primary input. Also works with plain keyword or topic.
  Run all stages in sequence when starting from scratch. Enter mid-pipeline if user
  provides an existing draft or only asks for one stage.
---

# Content Pipeline Pro

A complete pipeline for producing publish-ready, GEO-optimized blog content enriched with real community voice. Built for crypto/Web3 content teams.

## Pipeline

```
[0] X TREND MONITOR     → auto-run on session start, propose hot keywords
[1] KEYWORD RESEARCH    → scored, data-backed keyword selection
[2] CONTENT BRIEF       → outline mapped to keywords + UGC insertion points flagged
[3] UGC ENRICHMENT      → mine comments → ready-to-paste blog sections
[4] DRAFT               → human-style, data-backed, zero AI patterns
[5] SEO + GEO           → on-page checklist + AI-bot-friendly formatting
[6] QA REPORT           → rubric score + publish verdict
```

Enter at any stage. Run all 7 if starting from scratch with a spec + keyword. Start at Stage 5 if given an existing draft to optimize.

---

## Inputs

Required: `project_spec` (.md) + `keyword_or_topic`
Optional: `ugc_urls` (skip Stage 3 if absent), `blog_draft`, `language` (default: English), `word_count` (default: 1500–2000), `tone` (default: auto-detect from spec)

If `project_spec` is missing: stop and ask for it before starting.

---

## Stage 0 — X Trend Monitor

**Run automatically at the start of every new session, before the user says anything.**

1. Parse `project_spec.md` → extract: domain/niche, target audience, product themes, competitor names
2. Run these web searches (replace placeholders with spec values):
   - `site:x.com [domain keyword] -filter:replies`
   - `[domain keyword] trending twitter 2025`
   - `[domain keyword] discussion OR debate OR thread twitter`
   - `[competitor name] twitter sentiment 2025`
   - `crypto twitter trending today`
   - `[domain keyword] CT (crypto twitter) discussion`
3. Score each topic found:
   - Recency (30%): within 24h=10, 24–48h=7, older=3
   - Estimated engagement (30%): viral 1K+ signals=10, high=7, low=3
   - Relevance to spec (25%): direct=10, adjacent=6, weak=2
   - Debate/controversy signal (15%): active debate=10, one-sided=5, none=2
4. Keep top 3. Output before any user message:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔥 X TREND ALERT — [Today's Date]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Based on your project spec, here's what's hot on X right now:

TREND 1 (Score: X/10) 🔴 HOT
  Topic:             [topic]
  Why it's trending: [1-sentence reason]
  Blog angle:        [specific content angle]
  Suggested keyword: "[keyword]"
  X discussion:      "[paraphrased thread summary]"

TREND 2 (Score: X/10) 🟡 RISING
  Topic / Angle / Suggested keyword: [same format]

TREND 3 (Score: X/10) 🟢 WATCH
  Topic / Angle / Suggested keyword: [same format]

→ Say "go with Trend 1" and I'll run the full pipeline.
→ Or give me your own keyword and I'll start from Stage 1.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Fallback if web search off: skip Stage 0, say "Stage 0 unavailable — web search disabled. Provide a keyword to start Stage 1."
Fallback if no trends found: list 3 evergreen topics from spec context.

---

## Stage 1 — Keyword Research

1. Generate 8–12 seed keywords from topic + spec: head terms, mid-tail, long-tail question variants
2. For each seed keyword, run web searches:
   - `google trends [keyword] 2025` → trend direction + score
   - `site:x.com [keyword]` + `[keyword] trending twitter 2025` → buzz level + what people debate
   - `[keyword] search volume 2025` + `ubersuggest [keyword]` → volume estimate
   - Search `[keyword]` on Google → extract People Also Ask + Related Searches as long-tail candidates
3. Score each keyword:
   - Search volume (35%): <100=2, 100–1K=4, 1K–10K=7, 10K+=10
   - Keyword difficulty inverse (30%): Low=10, Medium=6, Hard=3
   - Google Trends direction (20%): Rising=9, Stable=6, Declining=2
   - X/Social buzz (15%): High=9, Medium=5, Low=2
4. Select: top 1 = primary, next 5–8 = secondary/LSI. Label all volume data `[estimated]`.
5. Ask once: "Do you have an Ahrefs or SEMrush API key for exact volume data?" Use if yes.

Output:
```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
KEYWORD RESEARCH RESULTS
PRIMARY KEYWORD (Score: X/10)
  Keyword / Volume / Difficulty / Trend / X Buzz / Search Intent: [values]

SECONDARY KEYWORDS:
┌─────────────────┬────────┬──────┬────────────┬──────────┬───────┐
│ Keyword         │ Volume │  KD  │ Trend      │ Buzz     │ Score │
└─────────────────┴────────┴──────┴────────────┴──────────┴───────┘

KEY INSIGHT FROM SOCIAL DATA: "[what people debate on X]"
CONTENT ANGLE: [unique angle based on trend signals + content gap]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Edge cases: keyword too broad → stop, suggest 3–5 long-tail alternatives. Keyword doesn't match spec → warn, ask for confirmation.

---

## Stage 2 — Content Brief & Outline

1. Pick flow pattern matching the keyword's search intent:
   - Problem → Solution (how-to, fixes)
   - What → Why → How (explainers)
   - Comparison (best X, X vs Y)
   - Journey (beginner guides)
   - Argument (opinion, trend analysis)

2. Map every long-tail keyword to a specific H2 or H3. Build this table first:
   ```
   [long-tail keyword] → H2: [section title]
   [long-tail keyword] → H3: [subsection title]
   [long-tail keyword] → FAQ: [question form]
   ```
   Section without keyword anchor = filler risk. Cut or merge.

3. Flag UGC insertion points in each H2:
   - Misconceptions debated on X → `← UGC: community counterpoints`
   - Recurring user questions → `← UGC: FAQ entry`
   - Real user experiences → `← UGC: case studies`

4. Output the brief and outline. After output, ask: "Does this outline look good? Any changes before I run UGC mining and write the draft?" Wait for confirmation before Stage 3.

Output includes: Target Keyword, Flow Pattern, Search Intent, Word Count, Audience, GEO Target (Perplexity / Google SGE / ChatGPT Search), Long-tail Keyword Map, UGC Insertion Points, full H1/H2/H3 outline with keyword markers 🔑 and UGC flags 💬, Keyword Coverage Check.

FAQ section in outline: minimum 5 Q&A entries. Mandatory for GEO.

---

## Stage 3 — UGC Enrichment

Skip if no `ugc_urls` provided. Note in QA report: "UGC: Missing."

Why this matters: Reddit = ~21% of Google AI Overview citations (early 2026). Real UGC = 2–3x more AI search visibility. E-E-A-T "Experience" signal = cannot be faked by AI-only content.

**For each URL in `ugc_urls`:**

1. `web_fetch` the page. Extract: original post body + all comments with engagement metrics (likes, upvotes, reply count, timestamp, nesting level).
   Fallback if login wall: "Could not access [URL]. Paste comment text directly."

2. Quality-score each comment (0–10):
   - Engagement/upvotes (30%): top 10%=10, top 25%=7, top 50%=5, bottom=2
   - Content length (20%): <10 words=1, 10–50=5, 50–150=8, 150+=10
   - Contains data/numbers (15%): yes=10, no=3
   - Personal experience markers (15%): "I tried...", "In my case..."=10, none=3
   - Substantive reply thread (10%): 3+ replies=10, 1–2=6, none=3
   - Sentiment strength (10%): strong opinion=8, neutral=4
   
   Score ≥6 → keep. Score <3 → discard (spam, memes, off-topic).

3. Classify each passing comment into exactly 1 of 3 categories:

   **Category A — Counter-Arguments**
   Qualifies: challenges original post, edge cases, overlooked downsides, "Yeah but...", "This ignores..."
   Output: 150–300 word balanced prose paragraph. Title: "Community Perspectives: Notable Counterpoints."
   Format: "[Main counterpoint]. According to discussions in the [platform] community, [elaboration with specifics]. However, [nuance]."
   Insert at: the H2 flagged `← UGC: community counterpoints`

   **Category B — Real-World FAQs**
   Qualifies: direct questions from comments (especially upvoted), repeated questions, questions original post didn't answer.
   Output: 3–6 Q&A pairs. Each answer synthesized from community + knowledge. Uncertain answers flagged: ⚠️ `[Suggested answer — verify before publishing]`
   Insert at: FAQ section

   **Category C — Personal Experiences**
   Qualifies: first-person accounts with specific numbers ("Saved 40% on fees..."), before/after, warnings from experience.
   Output: 2–4 mini case studies, 50–100 words each, professionally paraphrased — preserve original meaning and specific details, never fabricate.
   Format:
   ```
   **[Descriptive title]**
   [Paraphrased experience — original details preserved]
   — Source: [Platform] user | [X] likes/upvotes
   — Viral trigger: [data-backed claim / contrarian take / personal vulnerability / insider knowledge / simplification / prediction]
   ```
   Insert at: H2 flagged `← UGC: case studies`

   Never: fabricate comments, include usernames, include spam/memes/personal attacks, exceed 6 FAQs or 4 case studies.

4. Viral pattern analysis — for comments scoring ≥7, identify top 3 trigger types. Output 2 actionable writing tips for the draft.

5. Map every UGC block to its exact insertion point from Stage 2 outline.

Edge cases: <10 comments → process all + warn "limited data." All score <3 → "No high-value comments. Try a different URL." No comments section → "This URL has no comments. Paste a URL with discussion."

---

## Stage 4 — Draft Writing

Write the full article following the Stage 2 outline. Insert Stage 3 UGC blocks at flagged points.

**Before writing:**
- Meta Title: ≤60 chars, primary keyword near front, compelling
- Meta Description: ≤160 chars, primary keyword, hook included

**Introduction:**
- Open with specific fact, data point, or bold claim. Never a generic opener.
- Primary keyword within first 100 words.
- Place featured snippet candidate block here (40–60 words, direct definition or numbered steps — targets Google answer box).

**Body sections — for each H2:**
- Open with direct statement or specific fact (not a rhetorical question)
- Min 1 data point per major section. Source format: `[stat] — [Source, Year]`
- Find real stats first: search `[topic] statistics 2025`, `[topic] data report 2025`
- If no real data: insert `[DATA NEEDED: search "[suggested query]"]` — never invent statistics
- Primary keyword 1–2 times per section, natural placement
- Paragraphs: 3–4 lines max
- Insert UGC blocks at exact insertion points from Stage 2

**Conclusion:**
- Synthesize 2–3 key takeaways. Do not restate all H2s as bullet points.
- Clear, specific CTA. No new information.

**Internal links:** suggest 2–3, anchor text includes secondary keywords, note placement and destination.

**Tone (default for crypto/Web3):**
- Expert-to-peer: assumes reader knows basic crypto, not a developer
- Direct, confident, no hedging. Use "you."
- Vary sentence length. Define technical terms inline on first use.
- Minimum 3 data points per article total.

**AI patterns — never write any of these:**

Openers/fillers: "In today's fast-paced world" / "In the realm of" / "When it comes to" / "It's important to note" / "It goes without saying" / "Have you ever wondered" / "As we explore in this article" / "At the end of the day" / "Suffice it to say"

Inflated words: "Leverage" (abstract) / "Empower" / "Delve into" / "Dive into" / "Unlock the potential" / "Game-changer" / "Revolutionary" / "Transformative" / "Navigate the complexities"

Transitions: "Furthermore" / "Moreover" / "Additionally" / "In conclusion" / "Not only... but also" / "Both... and" (overused)

Represents-pattern: "[X] represents a..." → write "[X] is..." | "[X] represents the future of..." → state the specific change

Formatting: bullet dashes `- item` → use numbered lists or prose | em dashes `X — Y` → rewrite as 2 sentences or use comma/colon

Conclusion killers: "In conclusion" / "To summarize" / "We hope this article helped" / "The future of [X] is bright" / "Now is the time to embrace [X]"

If you catch yourself writing any of the above: stop and rewrite starting with a fact or direct claim.

Output format:
```md
# [H1 Title]
**Meta Title**: [≤60 chars]
**Meta Description**: [≤160 chars]
---
[Full article body — H2/H3 structure, UGC blocks inserted, data sourced]
---
**Internal Linking Suggestions:**
- "[anchor text]" → [destination page] — place in [section]
```

---

## Stage 5 — SEO + GEO Optimization

### SEO Checklist (fix gaps before Stage 6)

- [ ] Meta title: 50–60 chars, primary keyword near front
- [ ] Meta description: 150–160 chars, primary keyword, hook
- [ ] URL slug: short, lowercase, hyphenated, primary keyword
- [ ] H1 contains primary keyword (only one H1)
- [ ] H2s use secondary keywords or question variants
- [ ] Primary keyword in first 100 words
- [ ] Primary keyword in conclusion
- [ ] Primary keyword density: 1–1.5%
- [ ] LSI/semantic keywords distributed throughout
- [ ] 2–3 long-tail variants used
- [ ] Paragraphs ≤4 lines, no walls of text
- [ ] 2+ internal link suggestions noted
- [ ] 1–2 authoritative external sources noted
- [ ] Image alt text recommendations (min 2)
- [ ] FAQ present → FAQPage schema applicable
- [ ] How-to steps present → HowTo schema applicable

### GEO Rules (apply all 7 before finalizing)

GEO = Generative Engine Optimization. Goal: make content easy for AI agents (Perplexity, Google SGE, ChatGPT Search) to parse, extract, and cite.

**Rule 1 — Answer-first every H2**
Each H2 opens with 1–2 sentence direct answer before elaboration.
✅ "Liquid staking lets users stake ETH while keeping tokens liquid. You receive a receipt token (stETH) usable across DeFi."
❌ "When it comes to liquid staking, there are several aspects to consider..."

**Rule 2 — Explicit entity labeling**
Name entities with full context on first mention. Numbers include units: "3.2% APY" not "3.2%". Dates explicit: "as of Q1 2025" not "recently."

**Rule 3 — FAQ section mandatory (min 5 Q&A)**
Each answer: self-contained (readable without the rest of the article), 50–150 words, starts with direct answer then elaborates.

**Rule 4 — Featured snippet candidate block**
40–60 word definition or numbered steps for primary keyword. Placed within first H2. Format: clear paragraph OR numbered list, never mixed.

**Rule 5 — Citation-friendly formatting**
Every factual claim on its own sentence. Data: `[number] [unit] — [Source, Year]`. No pronoun ambiguity — name subjects explicitly. Use tables for comparisons (AI agents parse tables well).

**Rule 6 — Internal links use secondary keywords as anchor text**
Signals topical authority to Google and AI crawlers.

**Rule 7 — UGC sections present**
Confirm Stage 3 blocks are inserted. These provide E-E-A-T "Experience" signal.

GEO output block to include in Stage 6 report:
```
GEO OPTIMIZATION CHECKLIST
Answer-first structure (each H2):    ✅/❌
Explicit entity labeling:            ✅/❌
FAQ section present (min 5 Q&A):     ✅/❌
Featured snippet candidate block:    ✅/❌ — [paste 40–60 word block]
Citation-friendly formatting:        ✅/❌
Internal links use secondary KWs:    ✅/❌
UGC sections present (E-E-A-T):      ✅/❌ — [X sections]
Structured data suggestions:
  FAQPage schema:  ✅ → apply to FAQ section
  Article schema:  ✅ → apply to full post (datePublished, author, headline)
  HowTo schema:    ✅/❌ → if how-to steps present
  BreadcrumbList:  ✅ → for site navigation
AI-bot parse score: [X/10]
```

---

## Stage 6 — QA Scoring Report

Score the final article using this rubric (100 points total):

| Check | Points |
|---|---|
| Primary keyword in meta title | 10 |
| Primary keyword in H1 | 10 |
| Primary keyword in first 100 words | 10 |
| Keyword density (1–1.5%) | 15 |
| Meta title ≤60 chars | 10 |
| Meta description ≤160 chars | 10 |
| H2/H3 structure (min 3 H2s, logical flow) | 10 |
| Image alt text suggestions (min 2) | 5 |
| Internal linking suggestions (min 2) | 10 |
| Readability (paragraphs ≤4 lines) | 10 |

Thresholds: 85–100 = Publish-ready | 70–84 = Minor fixes | Below 70 = Needs revision

Output:
```
╔══════════════════════════════════════════════╗
║       CONTENT PIPELINE PRO — QA REPORT       ║
╚══════════════════════════════════════════════╝
ARTICLE: [Title] | KEYWORD: [primary] | WORDS: [X] | UGC: [X sections / None]

SEO SCORE: [X/100]
[Full checklist table with ✅/❌ and details per row]

GEO SCORE: [X/10]
[GEO checklist block from Stage 5]

WRITING QUALITY
  AI patterns detected: [count] — [list with location]
  Tone consistency:     [Consistent / Flags: section X drifts]
  Data points:          [X] — [meets / below minimum of 3]
  Fact-check flags:     [list all [VERIFY] and [DATA NEEDED]]

FINAL VERDICT
  SEO:     [Publish-ready / Minor fixes / Needs revision]
  GEO:     [Strong / Needs improvement]
  UGC:     [Enriched / Missing]
  VERDICT: [Publish-ready / Minor fixes / Needs revision]
  Actions: [list specific fixes with section references]
```

---

## Edge Cases

| Case | Action |
|---|---|
| `project_spec` missing | Stop. Ask for spec file before starting. |
| Keyword too broad | Stop. Suggest 3–5 long-tail alternatives. Wait for choice. |
| Keyword doesn't match spec | Warn. Ask for confirmation before continuing. |
| Deep technical content needed | Flag sections `[SME REVIEW]`. Never fabricate technical details. |
| User requests Vietnamese | Switch all output to Vietnamese. Keep all formats identical. |
| Word count <500 or >5000 | Warn. Recommend 800–2500 for this topic type. |
| SEO score below 70 | List specific fixes with section references. |
| Web search unavailable | Skip Stage 0. Flag stages that need it. Fall back to training knowledge, label `[estimated]`. |
| UGC URL behind login wall | Skip URL. Ask: "Paste comment text directly." |
| No high-value comments (all <3) | "No high-value comments. Try a different URL." |
| Fewer than 10 comments | Process all. Add: "Limited data — not representative." |
| No ugc_urls provided | Skip Stage 3. Mark UGC = Missing in QA. |
| Stage 0 finds no trends | List 3 evergreen topics from spec context. |
| User enters mid-pipeline | Start at appropriate stage. Ask what they have. |

---

## Limitations

- Stage 0 = simulated X monitoring via web search, not live X API
- Keyword volume = estimated unless user provides API key
- No automatic CMS publishing
- No image generation
- `[VERIFY]` and `[DATA NEEDED]` require human review before publishing
- SEO/GEO scores = internal rubric, not third-party tool scores
- UGC mining = public pages only, no login walls
