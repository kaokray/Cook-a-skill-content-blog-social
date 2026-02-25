# Scoring Rubrics — Auto Content Blog

---

## Stage 0 — Trend Scoring

| Signal | Weight | Scoring |
|---|---|---|
| Recency | 30% | Within 24h = 10, 24–48h = 7, older = 3 |
| Estimated engagement | 30% | Viral (1K+ likes signals) = 10, high = 7, low = 3 |
| Relevance to spec domain | 25% | Direct = 10, adjacent = 6, weak = 2 |
| Debate / controversy signal | 15% | Active debate = 10, one-sided = 5, none = 2 |

Keep top 3 scoring topics.

---

## Stage 1 — Keyword Scoring

| Signal | Weight | Scoring |
|---|---|---|
| Search volume | 35% | <100=2, 100–1K=4, 1K–10K=7, 10K+=10 |
| Keyword difficulty (inverse) | 30% | Low=10, Medium=6, Hard=3 |
| Google Trends direction | 20% | Rising=9, Stable=6, Declining=2 |
| X/Social buzz | 15% | High=9, Medium=5, Low=2 |

Select: highest score = primary keyword. Next 5–8 = secondary/LSI.

---

## Stage 3 — UGC Comment Quality Scoring

Score each comment 0–10:

| Signal | Weight | Scoring |
|---|---|---|
| Engagement (likes/upvotes) | 30% | Top 10% of thread=10, top 25%=7, top 50%=5, bottom=2 |
| Content length | 20% | <10 words=1, 10–50=5, 50–150=8, 150+=10 |
| Contains data/numbers | 15% | Yes=10, No=3 |
| Personal experience markers | 15% | "I tried...", "In my case..."=10, None=3 |
| Substantive reply thread | 10% | 3+ quality replies=10, 1–2=6, none=3 |
| Sentiment strength | 10% | Strong opinion=8, Neutral=4 |

Thresholds:
- Score ≥ 6 → High Value → include
- Score 3–5 → include only if < 20 high-value comments exist
- Score < 3 → discard (spam, memes, off-topic, too short)

---

## Stage 6 — SEO Score Rubric (100 points total)

| Check | Points | How to evaluate |
|---|---|---|
| Primary keyword in meta title | 10 | Exact or close match present |
| Primary keyword in H1 | 10 | Exact or close match present |
| Primary keyword in first 100 words | 10 | Check introduction paragraph |
| Keyword density (1–1.5%) | 15 | Count occurrences ÷ total word count |
| Meta title length (≤60 chars) | 10 | Count characters exactly |
| Meta description length (≤160 chars) | 10 | Count characters exactly |
| H2/H3 structure present and logical | 10 | Min 3 H2s, logical flow |
| Image alt text suggestions | 5 | Min 2 suggestions included |
| Internal linking suggestions | 10 | Min 2 suggestions included |
| Readability (paragraphs ≤4 lines) | 10 | No paragraph over 5 lines |

**Publish thresholds:**
- 85–100 → Publish-ready
- 70–84 → Minor fixes needed
- Below 70 → Needs revision

---

## Stage 5 — GEO Score (X/10)

Score 1 point for each rule met:

1. Answer-first structure applied to every H2
2. Explicit entity labeling throughout (names, numbers with units, dates)
3. FAQ section present with min 5 self-contained Q&A entries
4. Featured snippet candidate block written (40–60 words, placed in first H2)
5. Citation-friendly formatting (each claim on own sentence, data formatted `[number] [unit] — [Source, Year]`)
6. Internal links use secondary keywords as anchor text
7. UGC sections from Stage 3 inserted (E-E-A-T Experience signal)
8. FAQPage schema suggested
9. Article schema suggested
10. No pronoun ambiguity — all subjects named explicitly

Score 8–10 → GEO: Strong | Score 5–7 → GEO: Needs improvement | Below 5 → GEO: Weak
