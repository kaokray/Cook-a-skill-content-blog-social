# SKILL SPEC: Content Pipeline Pro
---

## Process

**Input**: Enter a keyword/topic and provide the project spec `.md` file.

### Phase 1 - Content Brief (~2 minutes)
The skill generates a detailed brief, including:
- target audience
- search intent
- outline
- tone
- word count
- reference angles
- CTA direction

### Phase 2 - Write Blog (~3 to 5 minutes)
The skill writes a full blog article based on the brief:
- correct structure
- consistent tone
- includes data/examples

### Phase 3 - Editor & QA (~2 minutes)
The skill reviews the draft and produces checks and suggestions:
- grammar
- tone consistency
- SEO score (keyword density, meta title/description, heading structure, readability)
- improvement recommendations

**Output**: Publish-ready blog article + SEO report + QA checklist  
**Total time**: 10 to 15 minutes per blog article (~90% faster)

---

## User

- **Primary**: Content Writer / SEO Writer  
- **Secondary**: Marketing Manager, Social Media Executive (needs content fast)  
- **Context**: Working in a crypto/Web3 content team that must ship blog posts regularly, with consistent tone and SEO optimization

---

## Input

## Required Inputs

| Field | Type | Description | Example |
|---|---|---|---|
| `keyword_or_topic` | string | Keyword or topic to write about | "what is liquid staking", "DeFi trends 2025" |
| `project_spec` | file (.md) | Project spec file containing product info, target audience, value prop, and tone of voice | `spec.md` for Project XYZ |

## Optional Inputs

| Field | Type | Description | Default |
|---|---|---|---|
| `language` | string | Language of the article | "English" |
| `word_count` | number | Desired word count | 1500-2000 |
| `tone` | string | Writing tone | Auto-detected from spec |
| `target_platform` | string | Publishing platform | "Blog/Website" |
| `additional_context` | string | Extra context or preferred angle | - |

---

## Output

## Phase 1 Output - Content Brief

```md
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
```

---

## Phase 2 Output - Blog Article

A complete blog article that includes:
- Meta Title (<=60 characters, includes the primary keyword)
- Meta Description (<=155 characters, includes the primary keyword)
- Blog body that follows the brief outline with clear H2/H3 structure
- A strong hook in the introduction
- Data, examples, and clear explanations in the body
- A conclusion with a CTA
- Internal linking suggestions (if the spec provides context)

---

## Phase 3 Output - QA Report

```md
# QA & SEO Report

## SEO Score: [X/100]

### SEO Checklist
| Check | Status | Details |
|-------|--------|---------|
| Primary keyword in title | âœ…/âŒ | [details] |
| Primary keyword in H1 | âœ…/âŒ | [details] |
| Primary keyword in first 100 words | âœ…/âŒ | [details] |
| Keyword density (1-2%) | âœ…/âŒ | [X%] |
| Meta title length (<=60 chars) | âœ…/âŒ | [X chars] |
| Meta description length (<=155 chars) | âœ…/âŒ | [X chars] |
| H2/H3 structure | âœ…/âŒ | [details] |
| Image alt text suggestions | âœ…/âŒ | [suggestions] |
| Internal linking opportunities | âœ…/âŒ | [suggestions] |
| Readability score | âœ…/âŒ | [score] |

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
- **Publish-ready?**: [Yes / Needs revision]
- **Key actions before publish**: [action list]
```

---

## Detailed Workflow

## Phase 1: Content Brief Generation

Input (keyword + spec)  
  -> Step 1: Parse `spec.md` -> extract product info, target audience, tone, value prop  
  -> Step 2: Analyze the keyword -> determine search intent and the best content type  
  -> Step 3: Build the keyword cluster -> primary, secondary, LSI keywords  
  -> Step 4: Review top-ranking content for the keyword -> find gaps and angles  
  -> Step 5: Generate the outline -> H2/H3 structure and key points per section  
  -> Step 6: Compile the Content Brief  
  -> Output: Content Brief (`.md`)

## Phase 2: Blog Writing

Input (Content Brief from Phase 1)  
  -> Step 1: Generate meta title + meta description (SEO-optimized)  
  -> Step 2: Write the introduction -> hook + context + thesis  
  -> Step 3: Write the body -> follow the outline, include data/examples, natural keyword placement  
  -> Step 4: Write the conclusion -> summary + CTA  
  -> Step 5: Add internal linking suggestions  
  -> Step 6: Format the final article (proper heading hierarchy, paragraph spacing)  
  -> Output: Complete Blog Article (`.md`)

## Phase 3: Editor & QA

Input (Blog Article from Phase 2 + Content Brief from Phase 1)  
  -> Step 1: SEO Audit -> check SEO criteria (keyword placement, density, meta tags, headings...)  
  -> Step 2: Grammar & Style Check -> spelling, grammar, sentence structure, word choice  
  -> Step 3: Tone Consistency Check -> compare article tone vs brief/spec tone  
  -> Step 4: Readability Assessment -> sentence length, paragraph length, jargon level  
  -> Step 5: Fact-check flags -> highlight claims that need verification  
  -> Step 6: Generate improvement suggestions  
  -> Step 7: Compile QA Report + Final Verdict  
  -> Output: QA & SEO Report (`.md`)

---

## Edge Cases

| Case | Handling |
|---|---|
| Keyword is too broad (example: "crypto") | Suggest 3-5 more specific long-tail keywords for the user to choose |
| Spec file is missing info (no tone, no target audience) | Use default assumptions and clearly flag what was assumed |
| Keyword does not match the project in the spec | Warn about the mismatch and ask the user to confirm before continuing |
| The article needs high technical depth | Flag sections that require SME (Subject Matter Expert) review |
| User wants Vietnamese | Support both English and Vietnamese, detect from input `language` |
| Word count is too short (<500) or too long (>5000) | Warn and recommend a word count range that fits the topic |
| QA detects major revisions are needed | Mark as "Needs revision" and list concrete fixes |

---

## Limitations (MVP)

- Keyword research is AI-based and does not pull real-time data from SEMrush/Ahrefs (unless web search is enabled)
- Does not automatically publish to a CMS
- Does not generate images for the blog
- Fact-checking only flags items and does not fully verify everything
- SEO score is an estimate based on best practices, not a third-party tool score

---

## Expansion Roadmap (if there is more time)

- Integrate SEO tools: connect Ahrefs/SEMrush APIs to pull real keyword data
- Auto-generate images: featured image and in-article images via AI
- Multi-format output: turn one blog into a Twitter thread, LinkedIn post, Telegram post
- Content Calendar: input multiple keywords and generate a full monthly calendar
- Performance tracking: track ranking and traffic after publish, then feed results back to improve
- Batch mode: input 10 keywords and output 10 blogs + 10 QA reports

---

## Tech Stack / Tools

- **Primary**: Claude Project (or a Custom GPT)
- **Skill format**: `SKILL.md` file with structured instructions
- **Input format**: `.md` file (spec) + text input (keyword/topic)
- **Output format**: `.md` files (brief, article, QA report)

---

## Success Metrics

| Metric | Before (Manual) | After (Skill) | Improvement |
|---|---|---|---|
| Time per blog article | 4-8 hours | 10-15 minutes | ~90% faster |
| Output consistency | Depends on writer | Same format every time | Consistent |
| SEO optimization | Manual checks, often missed | Automatic full checklist | Comprehensive |
| QA coverage | Self-review, easy to miss | Systematic checklist | Thorough |
| Scale capacity | 1-2 articles/day | 10+ articles/day | 5-10x |

