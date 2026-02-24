# Skill Card — Content Pipeline Pro

| Field | Details |
|---|---|
| **Skill Name** | Content Pipeline Pro |
| **What gets automated** | The full blog production workflow — from detecting trending topics on X, keyword research, content brief, mining real UGC from community discussions, writing a human-style draft, to SEO + GEO optimization and pre-publish QA scoring |
| **BEFORE: manual process** | Manual keyword research (~1h) → write brief (~30 min) → write draft (~3–5h) → self-check SEO (~30 min) → no UGC step, no GEO optimization. Total: **5–8 hours per article**. Output quality varies by writer. High chance of missing trends when offline. |
| **AFTER: with skill** | Open session → Stage 0 auto-proposes hot X trends → pick keyword → Stage 1–6 runs the pipeline → publish-ready blog article + QA report. Total: **15–25 minutes per article**. Consistent format every time. Real community UGC embedded. GEO-optimized for AI search engine citation. |
| **Tools / AI used** | Claude Project (SKILL.md as instruction), web search (Stage 0 trend monitor + Stage 1 keyword research + Stage 4 data sourcing), web_fetch (Stage 3 UGC mining from X/Reddit threads) |
| **Limitations** | Stage 0 is simulated monitoring via web search — not a live X API connection. Keyword volume is estimated unless user provides Ahrefs/SEMrush API key. Does not auto-publish to CMS. Does not generate images. UGC mining limited to publicly accessible pages. SEO/GEO scores are internal rubric estimates, not third-party tool scores. |
| **Expansion roadmap** | (1) Real X API integration for true 24/7 live monitoring. (2) Ahrefs/SEMrush API for exact keyword volume data. (3) Multi-format output: 1 blog → Twitter thread + LinkedIn post + Telegram post automatically. (4) Content Calendar: input 10 keywords → full monthly content plan. (5) Performance tracking: monitor post-publish ranking and traffic, feed results back to improve the skill. |
