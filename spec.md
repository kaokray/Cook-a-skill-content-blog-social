# SKILL SPEC: Content Pipeline Pro

## Problem Statement

Quy trình sản xuất blog trong team content (đặc biệt crypto/Web3) thường tốn nhiều thời gian và dễ thiếu consistency: brief không đủ chi tiết, bài viết lệch tone, SEO/QA check thủ công dễ miss edge cases. Skill này mục tiêu giảm mạnh thời gian end-to-end và chuẩn hóa output để publish-ready.

## Quy trình (High-level)

**Input**: Nhập `keyword/topic` + feed file spec `.md` của dự án.

### Phase 1 - Content Brief (~2 phút)
Skill tự generate brief chi tiết:
- target audience
- search intent
- outline
- tone
- word count
- reference angles
- CTA direction

### Phase 2 - Write Blog (~3-5 phút)
Skill viết bài blog hoàn chỉnh theo brief:
- đúng structure
- đúng tone
- có data/examples

### Phase 3 - Editor & QA (~2 phút)
Skill tự review bài viết:
- grammar
- tone consistency
- SEO score (keyword density, meta title/description, heading structure, readability)
- gợi ý cải thiện

**Output**: Bài blog publish-ready + SEO report + QA checklist  
**Tổng thời gian**: 10-15 phút / bài blog (giảm ~90% thời gian)

## User

- **Primary**: Content Writer / SEO Writer  
- **Secondary**: Marketing Manager, Social Media Executive (cần content nhanh)  
- **Context**: Làm việc trong team content của công ty crypto/Web3, cần output bài blog đều đặn, đúng tone, SEO-optimized

## Input

### Input bắt buộc

| Field | Type | Mô tả | Ví dụ |
|---|---|---|---|
| `keyword_or_topic` | string | Keyword hoặc topic cần viết bài | `"what is liquid staking"`, `"DeFi trends 2025"` |
| `project_spec` | file (.md) | File spec của dự án, chứa thông tin product, target audience, value prop, tone of voice | `spec.md` của dự án XYZ |

### Input tùy chọn (optional)

| Field | Type | Mô tả | Default |
|---|---|---|---|
| `language` | string | Ngôn ngữ bài viết | `"English"` |
| `word_count` | number | Số từ mong muốn | `1500-2000` |
| `tone` | string | Tone bài viết | Tự detect từ spec |
| `target_platform` | string | Platform đăng bài | `"Blog/Website"` |
| `additional_context` | string | Thông tin bổ sung, góc tiếp cận mong muốn | `-` |

## Output

## Phase 1 Output - Content Brief

```md
# Content Brief

## Basic Info
- **Target Keyword**: [keyword]
- **Search Intent**: [informational / navigational / transactional / commercial]
- **Target Audience**: [mô tả audience dựa trên spec]
- **Tone of Voice**: [detect từ spec hoặc input]
- **Word Count Target**: [số từ]

## Keyword Research
- **Primary Keyword**: [keyword chính]
- **Secondary Keywords**: [3-5 keyword phụ liên quan]
- **LSI Keywords**: [5-8 từ khóa ngữ nghĩa liên quan]
- **Questions People Ask**: [3-5 câu hỏi liên quan user hay search]

## Content Angle & Differentiation
- **Angle**: [góc tiếp cận chính]
- **What makes this different**: [điểm khác biệt so với bài competitor]
- **Key value for reader**: [reader được gì sau khi đọc]

## Outline
1. **[H2 Heading 1]**
   - Ý chính cần cover
   - Data/example gợi ý
2. **[H2 Heading 2]**
   - Ý chính cần cover
   - Data/example gợi ý
3. ... (tiếp tục)

## CTA Direction
- **CTA mục tiêu**: [người đọc làm gì sau khi đọc xong]
- **CTA placement**: [vị trí đặt CTA trong bài]

## References & Angles
- [Link/source tham khảo 1]
- [Link/source tham khảo 2]
```

## Phase 2 Output - Blog Article

Bài blog hoàn chỉnh bao gồm:
- Meta Title (≤60 ký tự, chứa primary keyword)
- Meta Description (≤155 ký tự, chứa primary keyword)
- Blog body đúng outline từ brief, có H2/H3 structure rõ ràng
- Introduction có hook mạnh
- Body có data, examples, giải thích rõ ràng
- Conclusion có CTA
- Internal linking suggestions (nếu có context từ spec)

## Phase 3 Output - QA Report

```md
# QA & SEO Report

## SEO Score: [X/100]

### SEO Checklist
| Check | Status | Details |
|-------|--------|---------|
| Primary keyword in title | ✅/❌ | [chi tiết] |
| Primary keyword in H1 | ✅/❌ | [chi tiết] |
| Primary keyword in first 100 words | ✅/❌ | [chi tiết] |
| Keyword density (1-2%) | ✅/❌ | [X%] |
| Meta title length (≤60 chars) | ✅/❌ | [X chars] |
| Meta description length (≤155 chars) | ✅/❌ | [X chars] |
| H2/H3 structure | ✅/❌ | [chi tiết] |
| Image alt text suggestions | ✅/❌ | [gợi ý] |
| Internal linking opportunities | ✅/❌ | [gợi ý] |
| Readability score | ✅/❌ | [score] |

### Grammar & Style Check
| Issue | Location | Suggestion |
|-------|----------|------------|
| [loại lỗi] | [vị trí] | [gợi ý sửa] |

### Tone Consistency
- **Expected tone**: [tone từ brief]
- **Assessment**: [đánh giá tone có consistent không]
- **Flags**: [đoạn nào lệch tone, nếu có]

### Improvement Suggestions
1. [Gợi ý cải thiện 1]
2. [Gợi ý cải thiện 2]
3. [Gợi ý cải thiện 3]

### Final Verdict
- **Publish-ready?**: [Yes / Needs revision]
- **Key actions before publish**: [danh sách action nếu cần]
```

## Workflow chi tiết

### Phase 1: Content Brief Generation

Input (keyword + spec)
- Step 1: Parse `spec.md` -> extract product info, target audience, tone, value prop
- Step 2: Analyze keyword -> xác định search intent, content type phù hợp
- Step 3: Research keyword cluster -> primary, secondary, LSI keywords
- Step 4: Analyze top-ranking content cho keyword đó -> tìm gaps & angles
- Step 5: Generate outline -> H2/H3 structure, key points per section
- Step 6: Compile Content Brief

Output: Content Brief (`.md`)

### Phase 2: Blog Writing

Input (Content Brief from Phase 1)
- Step 1: Generate meta title + meta description (SEO-optimized)
- Step 2: Write introduction -> hook + context + thesis
- Step 3: Write body -> follow outline, include data/examples, natural keyword placement
- Step 4: Write conclusion -> summary + CTA
- Step 5: Add internal linking suggestions
- Step 6: Format final article (proper heading hierarchy, paragraph spacing)

Output: Complete Blog Article (`.md`)

### Phase 3: Editor & QA

Input (Blog Article from Phase 2 + Content Brief from Phase 1)
- Step 1: SEO Audit -> check tất cả tiêu chí SEO (keyword placement, density, meta tags, headings...)
- Step 2: Grammar & Style Check -> spelling, grammar, sentence structure, word choice
- Step 3: Tone Consistency Check -> so sánh tone bài viết vs tone trong brief/spec
- Step 4: Readability Assessment -> sentence length, paragraph length, jargon level
- Step 5: Fact-check flags -> highlight claims cần verify
- Step 6: Generate Improvement Suggestions
- Step 7: Compile QA Report + Final Verdict

Output: QA & SEO Report (`.md`)

## Edge Cases

| Case | Handling |
|---|---|
| Keyword quá broad (ví dụ: `"crypto"`) | Skill gợi ý 3-5 long-tail keyword cụ thể hơn để user chọn |
| Spec file thiếu thông tin (không có tone, không có target audience) | Skill dùng default assumptions + flag cho user biết đang assume gì |
| Keyword không liên quan đến project trong spec | Skill cảnh báo mismatch, hỏi user confirm trước khi tiếp tục |
| Bài viết cần technical depth cao | Skill flag những phần cần SME (Subject Matter Expert) review |
| User muốn viết bài tiếng Việt | Skill support cả English và Vietnamese, detect từ input language |
| Word count quá ngắn (<500) hoặc quá dài (>5000) | Skill cảnh báo và gợi ý word count phù hợp với topic |
| QA phát hiện bài cần major revision | Output rõ `"Needs revision"` + list cụ thể cần sửa gì |

## Limitations (MVP)

- Keyword research dựa trên kiến thức của AI, không pull data real-time từ SEMrush/Ahrefs (trừ khi có web search)
- Không tự động publish lên CMS
- Không tự generate hình ảnh cho bài blog
- Fact-check chỉ flag, không tự verify 100%
- SEO score là ước tính dựa trên best practices, không phải score từ tool chuyên dụng

## Roadmap mở rộng (nếu có thêm thời gian)

- Integration với SEO tools: Kết nối Ahrefs/SEMrush API để pull keyword data thật
- Auto-generate images: Tạo featured image + in-article images bằng AI
- Multi-format output: Từ 1 blog -> auto-generate Twitter thread, LinkedIn post, Telegram post
- Content Calendar: Input nhiều keywords -> output content calendar cho cả tháng
- Performance tracking: Sau khi publish, track ranking + traffic -> feedback loop để improve skill
- Batch mode: Input danh sách 10 keywords -> output 10 bài blog + 10 QA reports

## Tech Stack / Tools

- **Primary**: Claude Project (hoặc Custom GPT)
- **Skill format**: `SKILL.md` file với structured instructions
- **Input format**: `.md` file (spec) + text input (keyword/topic)
- **Output format**: `.md` files (brief, article, QA report)

## Success Metrics

| Metric | Before (Manual) | After (Skill) | Improvement |
|---|---|---|---|
| Thời gian / bài blog | 4-8 giờ | 10-15 phút | ~90% faster |
| Output consistency | Tuỳ người viết | Chuẩn format mỗi lần | Consistent |
| SEO optimization | Check thủ công, hay miss | Auto-check đầy đủ | Comprehensive |
| QA coverage | Tự review, dễ bỏ sót | Systematic checklist | Thorough |
| Scale capacity | 1-2 bài/ngày | 10+ bài/ngày | 5-10x |
