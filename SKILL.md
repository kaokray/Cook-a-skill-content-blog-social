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

End-to-end pipeline: trending topic → keyword research → brief → UGC enrichment → human-style draft → SEO + GEO optimization → scored QA report.

## Pipeline

```
[0] X TREND MONITOR  → auto-run on session start, propose hot keywords
[1] KEYWORD RESEARCH → scored, data-backed selection
[2] CONTENT BRIEF    → outline + keyword map + UGC insertion points
[3] UGC ENRICHMENT   → mine comments → ready-to-paste blog sections
[4] DRAFT            → human-style, data-backed, zero AI patterns
[5] SEO + GEO        → on-page checklist + AI-bot-friendly formatting
[6] QA REPORT        → rubric score + publish verdict
```

Enter at any stage. Run all 7 from scratch. Start at Stage 5 for existing drafts.

**Quick commands:**
- `run full pipeline` → Stage 0 → Stage 6
- `start from stage [N]` → enter at any stage
- `score my draft` → Stage 5 → Stage 6

**Reference files** (read when detail is needed):
- `references/scoring-rubrics.md` — all scoring tables (trend, keyword, UGC, SEO, GEO)
- `references/ai-patterns-blacklist.md` — full list of AI phrases to never write
- `references/output-templates.md` — exact output format for each stage
- `references/example-run.md` — real example: keyword "what is liquid staking"

---

## Inputs

Required: `project_spec` (.md) + `keyword_or_topic`
Optional: `ugc_urls` (skip Stage 3 if absent), `blog_draft`, `language` (default: English), `word_count` (default: 1500–2000), `tone` (default: auto-detect from spec)

If `project_spec` is missing: stop and ask for it before starting.

---

## Stage 0 — X Trend Monitor

**Run automatically at the start of every new session, before the user says anything.**

1. Parse `project_spec.md` → extract: domain/niche, audience, product themes, competitor names
2. Run web searches (fill in values from spec):
   - `site:x.com [domain keyword] -filter:replies`
   - `[domain keyword] trending twitter 2025`
   - `[domain keyword] discussion OR debate twitter`
   - `[competitor name] twitter sentiment 2025`
   - `crypto twitter trending today`
   - `[domain keyword] CT crypto twitter discussion`
3. Score each topic → see `references/scoring-rubrics.md` Stage 0
4. Keep top 3. Output Trend Alert before any user message → see `references/output-templates.md` Stage 0

Fallback if web search off: skip, say "Stage 0 unavailable. Provide a keyword to start Stage 1."
Fallback if no trends found: list 3 evergreen topics from spec context.

---

## Stage 1 — Keyword Research

1. Generate 8–12 seed keywords: head terms, mid-tail, long-tail question variants
2. For each seed, run:
   - `google trends [keyword] 2025` → direction
   - `site:x.com [keyword]` + `[keyword] trending twitter 2025` → buzz + debate angle
   - `[keyword] search volume 2025` + `ubersuggest [keyword]` → volume estimate
   - Search `[keyword]` → extract People Also Ask + Related Searches
3. Score using rubric → see `references/scoring-rubrics.md` Stage 1
4. Select top 1 = primary, next 5–8 = secondary/LSI. Label volume as `[estimated]`.
5. Ask once: "Do you have an Ahrefs or SEMrush API key?" Use if provided.
6. Output → see `references/output-templates.md` Stage 1

Edge cases: keyword too broad → suggest 3–5 long-tail alternatives. Doesn't match spec → warn + confirm.

---

## Stage 2 — Content Brief & Outline

1. Pick flow pattern:
   - Problem → Solution | What → Why → How | Comparison | Journey | Argument
2. Map every long-tail keyword to H2, H3, or FAQ entry. No section without a keyword anchor.
3. Flag UGC insertion points: `← UGC: community counterpoints` / `← UGC: case studies` / `← UGC: FAQ`
4. Output brief + outline → see `references/output-templates.md` Stage 2
5. Ask: "Does this outline look good?" Wait for confirmation before Stage 3.

FAQ section: minimum 5 entries. Mandatory for GEO.

---

## Stage 3 — UGC Enrichment

Skip if no `ugc_urls`. Note "UGC: Missing" in QA report.

Why it matters: Reddit ~21% of Google AI Overview citations. Real UGC = 2–3x AI search visibility. E-E-A-T "Experience" signal = cannot be faked by AI content.

For each URL:
1. `web_fetch` → extract post body + all comments with engagement metrics
   - Fallback if login wall: "Paste comment text directly"
2. Quality-score each comment → see `references/scoring-rubrics.md` Stage 3
3. Classify into 3 categories:
   - **Category A — Counter-Arguments**: challenges original post, edge cases, "Yeah but..." → 150–300 word prose paragraph
   - **Category B — Real-World FAQs**: direct questions from comments, especially upvoted or repeated → 3–6 Q&A pairs
   - **Category C — Personal Experiences**: first-person accounts with specific numbers/outcomes → 2–4 mini case studies, 50–100 words each, paraphrased but never fabricated
4. Viral pattern analysis for comments scoring ≥7: identify top 3 trigger types, output 2 writing tips
5. Map each UGC block to its insertion point from Stage 2 outline
6. Output → see `references/output-templates.md` Stage 3

Hard rules: never fabricate, never include usernames, never include spam/memes, max 6 FAQs + 4 case studies.

Edge cases: <10 comments → warn "limited data". All score <3 → "No high-value comments, try different URL."

---

## Stage 4 — Draft Writing

Write full article: follow Stage 2 outline exactly, insert Stage 3 UGC blocks at flagged points.

**Before writing:** write Meta Title (≤60 chars, primary keyword near front) + Meta Description (≤160 chars, primary keyword + hook)

**Intro:** specific fact or bold claim opener. Primary keyword within first 100 words. Write featured snippet candidate block (40–60 words, direct definition or numbered steps) — place within first H2.

**Body:** answer-first each H2 (1–2 sentence direct answer before elaboration). Min 1 data point per major section. Find real stats first: search `[topic] statistics 2025`. If unavailable: `[DATA NEEDED: search "[query]"]`. Source format: `stat — Source, Year`. UGC blocks at exact insertion points.

**Data minimum:** 3 data points total per article. Never invent statistics.

**Paragraphs:** 3–4 lines max. Define technical terms inline on first use.

**AI patterns:** never write any phrase from `references/ai-patterns-blacklist.md`. If caught: stop, rewrite with fact or direct claim.

**Conclusion:** synthesize 2–3 takeaways. Do not restate all H2s as bullet points. Specific CTA.

**Internal links:** suggest 2–3, anchor text uses secondary keywords.

Output format → see `references/output-templates.md` Stage 4

---

## Stage 5 — SEO + GEO Optimization

### SEO Checklist
- [ ] Meta title: 50–60 chars, primary keyword near front
- [ ] Meta description: 150–160 chars, primary keyword, hook
- [ ] H1 contains primary keyword (only one H1)
- [ ] H2s use secondary keywords or question variants
- [ ] Primary keyword in first 100 words and in conclusion
- [ ] Keyword density: 1–1.5%
- [ ] Paragraphs ≤4 lines
- [ ] 2+ internal link suggestions (anchor text = secondary keywords)
- [ ] 1–2 external authoritative sources noted
- [ ] Image alt text recommendations (min 2)
- [ ] FAQ present → FAQPage schema | How-to steps → HowTo schema

### GEO Rules (apply all 7)

GEO = Generative Engine Optimization. Goal: easy for Perplexity, Google SGE, ChatGPT Search to parse and cite.

1. **Answer-first every H2** — 1–2 sentence direct answer before elaboration
2. **Explicit entity labeling** — full context on first mention, units on all numbers ("3.2% APY"), explicit dates ("as of Q1 2025")
3. **FAQ mandatory (min 5)** — each answer self-contained, 50–150 words, direct answer first
4. **Featured snippet block** — 40–60 words, placed within first H2, paragraph OR numbered list (not mixed)
5. **Citation-friendly** — each factual claim on its own sentence, data formatted `number unit — Source, Year`, no pronoun ambiguity
6. **Secondary keywords in internal link anchor text**
7. **UGC sections present** — confirms E-E-A-T "Experience" signal

GEO output block → see `references/output-templates.md` Stage 5
Scoring rubric → see `references/scoring-rubrics.md` Stage 5

---

## Stage 6 — QA Scoring Report

Score using 100-point rubric → see `references/scoring-rubrics.md` Stage 6

Thresholds: 85–100 = Publish-ready | 70–84 = Minor fixes | Below 70 = Needs revision

Output format → see `references/output-templates.md` Stage 6

---

## Edge Cases

| Case | Action |
|---|---|
| `project_spec` missing | Stop. Ask for spec before starting. |
| Keyword too broad | Stop. Suggest 3–5 long-tail alternatives. Wait for choice. |
| Keyword doesn't match spec | Warn. Ask for confirmation. |
| Deep technical content | Flag `[SME REVIEW]`. Never fabricate. |
| User requests Vietnamese | Switch all output to Vietnamese. Same formats. |
| Word count <500 or >5000 | Warn. Recommend 800–2500. |
| SEO score below 70 | List specific fixes with section references. |
| Web search unavailable | Skip Stage 0. Flag affected stages. Fall back to training knowledge, label `[estimated]`. |
| UGC URL behind login wall | Skip URL. Ask: "Paste comment text directly." |
| No high-value UGC comments | "No high-value comments. Try a different URL." |
| No ugc_urls provided | Skip Stage 3. Mark UGC = Missing in QA. |
| Stage 0 finds no trends | List 3 evergreen topics from spec context. |
| User enters mid-pipeline | Start at appropriate stage. Ask what they have. |

---

## Limitations

- Stage 0: simulated X monitoring via web search, not live X API
- Keyword volume: estimated unless user provides API key
- No CMS auto-publishing, no image generation
- `[VERIFY]` and `[DATA NEEDED]` require human review before publishing
- SEO/GEO scores: internal rubric, not third-party tool scores
- UGC mining: public pages only
