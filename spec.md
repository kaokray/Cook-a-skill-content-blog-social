Mình sẽ bổ sung đúng 4 điểm Supervisor feedback vào spec của bạn. Đây là bản hoàn chỉnh:

SKILL SPEC: Content Pipeline Pro

Process
Input: Enter a keyword/topic and provide the project spec .md file.
Phase 1 - Content Brief (~2 minutes)
The skill generates a detailed brief, including:
target audience
search intent
outline
tone
word count
reference angles
CTA direction
Phase 2 - Write Blog (~3 to 5 minutes)
The skill writes a full blog article based on the brief:
correct structure
consistent tone
includes data/examples
Phase 3 - Editor & QA (~2 minutes)
The skill reviews the draft and produces checks and suggestions:
grammar
tone consistency
SEO score (keyword density, meta title/description, heading structure, readability)
improvement recommendations
Output: Publish-ready blog article + SEO report + QA checklist Total time: 10 to 15 minutes per blog article (~90% faster)

User
Primary: Content Writer / SEO Writer
Secondary: Marketing Manager, Social Media Executive (needs content fast)
Context: Working in a crypto/Web3 content team that must ship blog posts regularly, with consistent tone and SEO optimization

Input
Required Inputs
Field
Type
Description
Example
keyword_or_topic
string
Keyword or topic to write about
"what is liquid staking", "DeFi trends 2025"
project_spec
file (.md)
Project spec file containing product info, target audience, value prop, and tone of voice
spec.md for Project XYZ

Optional Inputs
Field
Type
Description
Default
language
string
Language of the article
"English"
word_count
number
Desired word count
1500–2000
tone
string
Writing tone
Auto-detected from spec
target_platform
string
Publishing platform
"Blog/Website"
additional_context
string
Extra context or preferred angle
—


Output
Phase 1 Output - Content Brief
# Content Brief

## Basic Info
- **Target Keyword**: [keyword]
- **Search Intent**: [informational / navigational / transactional / commercial]
- **Target Audience**: [describe audience based on spec]
- **Tone of Voice**: [detected from spec or from input]
- **Word Count Target**: [word count]

## Keyword Research
- **Primary Keyword**: [main keyword]
- **Secondary Keywords**: [3-5 related keywords]
- **LSI Keywords**: [5-8 semantically related keywords]
- **Questions People Ask**: [3-5 common search questions]

## Content Angle & Differentiation
- **Angle**: [main angle]
- **What makes this different**: [how it differs from competitor content]
- **Key value for reader**: [what the reader gets after reading]

## Outline
1. **[H2 Heading 1]**
   - Key points to cover
   - Suggested data/examples
2. **[H2 Heading 2]**
   - Key points to cover
   - Suggested data/examples
3. ... (continue)

## CTA Direction
- **CTA goal**: [what the reader should do next]
- **CTA placement**: [where the CTA should appear]

## References & Angles
- [Reference/source 1]
- [Reference/source 2]


Phase 2 Output - Blog Article
A complete blog article that includes:
Meta Title (≤60 characters, includes the primary keyword)
Meta Description (≤155 characters, includes the primary keyword)
Blog body that follows the brief outline with clear H2/H3 structure
A strong hook in the introduction
Data, examples, and clear explanations in the body
A conclusion with a CTA
Internal linking suggestions (if the spec provides context)

Phase 3 Output - QA Report
# QA & SEO Report

## SEO Score: [X/100]

### SEO Checklist
| Check | Points | Status | Details |
|-------|--------|--------|---------|
| Primary keyword in title | 10 | ✅/❌ | [details] |
| Primary keyword in H1 | 10 | ✅/❌ | [details] |
| Primary keyword in first 100 words | 10 | ✅/❌ | [details] |
| Keyword density (1–2%) | 15 | ✅/❌ | [X%] |
| Meta title length (≤60 chars) | 10 | ✅/❌ | [X chars] |
| Meta description length (≤155 chars) | 10 | ✅/❌ | [X chars] |
| H2/H3 structure present | 10 | ✅/❌ | [details] |
| Image alt text suggestions | 5 | ✅/❌ | [suggestions] |
| Internal linking opportunities | 10 | ✅/❌ | [suggestions] |
| Readability score | 10 | ✅/❌ | [score] |

**Scoring thresholds:**
- 85–100: Publish-ready
- 70–84: Minor fixes needed
- Below 70: Needs revision

### Grammar & Style Check
| Issue | Location | Suggestion |
|-------|----------|------------|
| [issue type] | [location] | [fix suggestion] |

### Tone Consistency
- **Expected tone**: [tone from brief]
- **Assessment**: [is the tone consistent]
- **Flags**: [sections that drift off-tone, if any]

### Improvement Suggestions
1. [Suggestion 1]
2. [Suggestion 2]
3. [Suggestion 3]

### Final Verdict
- **Publish-ready?**: [Yes / Minor fixes / Needs revision]
- **Key actions before publish**: [action list]


Detailed Workflow
Phase 1: Content Brief Generation
Input (keyword + spec)
  -> Step 1: Parse spec.md -> extract product info, target audience, tone, value prop
  -> Step 2: Analyze the keyword -> determine search intent and best content type
  -> Step 3: Keyword research using web search
       - Search queries to run:
           "[keyword] search volume 2025"
           "people also ask [keyword]"
           "[keyword] related keywords"
           "[keyword] crypto/Web3" (if domain-specific)
       - From results, extract and rank keywords by:
           Relevance to the spec's product and audience (primary filter)
           Search frequency signals found in results (secondary filter)
           Long-tail specificity (prefer specific over generic)
       - Assign each keyword a relevance tier: Primary / Secondary / LSI
  -> Step 4: Competitor content analysis using web search
       - Search query: "[keyword]" -> identify top 3–5 ranking results
       - Fetch each result and analyze:
           Heading structure (H2/H3 depth and topics covered)
           Approximate word count
           Subtopics covered vs. subtopics missing
           Tone: beginner-friendly vs. technical
       - Identify content gaps: subtopics the competitors do not cover or cover poorly
       - Use gaps to define the differentiation angle for this article
  -> Step 5: Generate outline -> H2/H3 structure and key points per section,
             prioritizing gap topics identified in Step 4
  -> Step 6: Compile the Content Brief
  -> Output: Content Brief (.md)


Phase 2: Blog Writing
Input (Content Brief from Phase 1)
  -> Step 1: Generate meta title + meta description (SEO-optimized)
  -> Step 2: Write the introduction -> hook + context + thesis
  -> Step 3: Write the body -> follow the outline
       Data requirements:
         - Minimum 3 statistics or data points per article
         - Data sourced from: web search, the spec file, or clearly flagged as illustrative
         - Each major claim should be supported by a number, example, or case
  -> Step 4: Apply Writing Principles (see section below)
  -> Step 5: Write the conclusion -> summary + CTA
  -> Step 6: Add internal linking suggestions
  -> Step 7: Format the final article (proper heading hierarchy, paragraph spacing)
  -> Output: Complete Blog Article (.md)

Writing Principles for Phase 2
Tone guide (default for crypto/Web3 content):
Write expert-to-peer: assume the reader knows basic crypto concepts but is not a developer
Be direct and confident — avoid hedging language
Use short sentences and paragraphs (3–4 lines max per paragraph)
Avoid jargon without explanation; when using technical terms, define them inline on first use
Data requirements:
Minimum 3 data points per article (stats, percentages, on-chain figures, market numbers)
Source data from web search or the spec file; if neither is available, flag the claim with [VERIFY]
AI-pattern avoidance — never use the following:
"In today's fast-paced world..."
"It's important to note that..."
"Furthermore," / "Moreover," / "In conclusion,"
"As we navigate the ever-evolving landscape of..."
"It goes without saying..."
"Delve into" / "Dive into"
Generic rhetorical questions as section openers ("Have you ever wondered...?")
Filler affirmations ("Absolutely!" / "Great question!")
Instead: open sections with a direct statement or a specific fact. Let the data and examples carry the weight.

Phase 3: Editor & QA
Input (Blog Article from Phase 2 + Content Brief from Phase 1)
  -> Step 1: SEO Audit -> score each checklist item using the rubric (see QA Report section)
  -> Step 2: Grammar & Style Check -> spelling, grammar, sentence structure, word choice
  -> Step 3: Tone Consistency Check -> compare article tone vs. brief/spec tone
  -> Step 4: Readability Assessment -> sentence length, paragraph length, jargon level
  -> Step 5: Fact-check flags -> highlight claims with [VERIFY] that need human confirmation
  -> Step 6: AI-pattern scan -> flag any phrases from the avoidance list that slipped through
  -> Step 7: Generate improvement suggestions
  -> Step 8: Compile QA Report + Final Verdict using scoring thresholds
  -> Output: QA & SEO Report (.md)


Edge Cases
Case
Handling
Keyword is too broad (e.g., "crypto")
Suggest 3–5 more specific long-tail keywords for the user to choose
Spec file is missing info (no tone, no target audience)
Use default assumptions and clearly flag what was assumed
Keyword does not match the project in the spec
Warn about the mismatch and ask the user to confirm before continuing
The article needs high technical depth
Flag sections that require SME (Subject Matter Expert) review with [SME REVIEW]
User wants Vietnamese
Support both English and Vietnamese, detect from input language
Word count is too short (<500) or too long (>5000)
Warn and recommend a word count range that fits the topic
QA detects major revisions are needed (score <70)
Mark as "Needs revision" and list concrete fixes with section references
Web search returns no useful results for keyword research
Fall back to AI knowledge base and flag: "Keyword data based on training knowledge, not live search"
Competitor content is behind a paywall or not fetchable
Skip that URL, move to next result, note it was skipped


Limitations (MVP)
Keyword research uses web search when enabled; if web search is off, AI falls back to training knowledge (flagged clearly in output)
Does not pull real-time data from SEMrush/Ahrefs APIs
Does not automatically publish to a CMS
Does not generate images for the blog
Fact-checking flags items with [VERIFY] but does not fully verify every claim
SEO score is calculated against the internal rubric, not a third-party tool score
Competitor analysis limited to publicly accessible pages (paywalled content is skipped)

Expansion Roadmap (if there is more time)
Integrate SEO tools: connect Ahrefs/SEMrush APIs to pull real keyword volume data
Auto-generate images: featured image and in-article images via AI image generation
Multi-format output: turn one blog into a Twitter thread, LinkedIn post, Telegram post
Content Calendar: input multiple keywords and generate a full monthly content calendar
Performance tracking: track ranking and traffic after publish, feed results back to refine the skill
Batch mode: input 10 keywords and output 10 blogs + 10 QA reports

Tech Stack / Tools
Primary: Claude Project (or Custom GPT)
Skill format: SKILL.md file with structured instructions
Web search: enabled for keyword research and competitor analysis in Phase 1
Input format: .md file (spec) + text input (keyword/topic)
Output format: .md files (brief, article, QA report)

Success Metrics
Metric
Before (Manual)
After (Skill)
Improvement
Time per blog article
4–8 hours
10–15 minutes
~90% faster
Output consistency
Depends on writer
Same format every time
Consistent
SEO optimization
Manual checks, often missed
Automatic scored checklist
Comprehensive
QA coverage
Self-review, easy to miss
Systematic checklist with rubric
Thorough
Scale capacity
1–2 articles/day
10+ articles/day
5–10x



