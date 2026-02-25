---
name: viral-remix
description: Find posts that already went viral in other markets or adjacent niches, then adapt them for the active brand. Use when the user wants to maximize success by remixing proven content.
user-invocable: true
argument-hint: [topic] [--market US|FR|ES|DE|UK|BR] [--platform linkedin|tiktok|instagram] [--format post|carousel|video] [--count N]
allowed-tools: Read, Write, Glob, Grep, WebSearch, WebFetch
---

# Skill: Viral Remix

## Instructions

When the user invokes `/viral-remix`, find posts that have already gone viral in the same niche but different geographic markets (or in adjacent niches), then adapt them for the active brand. The goal is to maximize success probability by reusing proven content structures, hooks, and angles.

**This is NOT `/content-ideas`** (which finds inspiration) or **`/linkedin-post`** (which generates from scratch). This skill specifically hunts for **proven viral content** and creates near-copies adapted to the brand's voice, language, and market.

**Default active brand**: ai-social-media-manager (`brands/ai-social-media-manager/`). For other brands, specify `--brand [name]`.

### Step 1 — Load Context
ALWAYS read these files from the active brand before doing anything:
- `brands/[brand]/brand-voice.md` — voice, identity, golden rules
- `brands/[brand]/audience-personas.md` — target personas
- `brands/[brand]/tone-guide.md` (or `tono-infotainment.md` for legacy brands) — tone, humor, linguistic patterns
- `brands/[brand]/content-pillars.md` — pillars and editorial calendar
- `framework/ai-detection-signals.md` — AI detection red flags to avoid in adapted text
- `framework/content-frameworks.md` — frameworks L1-L8 (LinkedIn) + V1-V6 (Video)

### Step 2 — Parse Arguments
The user provides a **topic** (required) and optionally:
- `--market [US|FR|ES|DE|UK|BR|IT|...]`: which geographic market(s) to search in. Default: search US, UK, and 1-2 EU markets automatically
- `--platform [linkedin|tiktok|instagram]`: default `linkedin`
- `--format [post|carousel|video]`: default `post`
- `--count N`: how many viral posts to find. Default: 5

### Step 2b — Detect Language
Determine the language for the adapted content:
1. Read the `Language:` field from the brand's `brand-voice.md`
2. If specified, use that language without asking
3. If not specified, detect the language of the conversation
4. If the user is speaking a language different from English and no brand language is set, ask: "I notice you're speaking [language]. Should I generate adapted content in [language]?"

### Step 3 — Multi-Market Viral Research
This is the core differentiator. Run multiple `WebSearch` queries in a structured pattern:

**3a) Same niche, different markets**
Search for viral posts on the topic in 3-4 geographic markets. Prioritize markets where the brand's niche is more mature or competitive (usually US/UK first, then EU).

Query patterns:
- `"viral LinkedIn post" [topic] [market] 2025 2026`
- `"LinkedIn post" [topic] "likes" OR "comments" OR "impressions" [market]`
- `site:linkedin.com [topic] [language-keyword]`
- `"best LinkedIn posts" [niche] [year]`
- `[topic] "went viral" LinkedIn [market]`

**3b) Adjacent niches, any market**
Search for viral posts on related topics that share the same emotional trigger or audience pain point. Think laterally: what other industries face the same frustration, transformation, or controversy?

Query patterns:
- `"viral LinkedIn post" [adjacent-topic] 2025 2026`
- `[related-niche] "LinkedIn" "viral" OR "millions of views"`

**3c) Same format, any niche**
Search for viral structural formats (e.g., "contrarian take" posts, "before/after" posts, "unpopular opinion" posts) that can be reskinned to the brand's niche.

Query patterns:
- `"unpopular opinion" LinkedIn viral [year]`
- `"hot take" LinkedIn [niche-adjacent] viral`
- `"contrarian" LinkedIn post viral [year]`
- `LinkedIn "carousel" viral [topic-adjacent] [year]` (if format is carousel)

**Research tips**:
- Run at least 4-6 distinct WebSearch queries
- If a query returns no useful results, try alternative phrasing
- Look for roundup articles ("best LinkedIn posts of 2025") — they aggregate proven content
- WebFetch on promising URLs to get full post text when available

### Step 4 — Analyze & Score Each Viral Post
For each post found, extract and present:
- **Original content**: the post text (or a summary if full text not available)
- **Original author**: name, niche, market/country
- **Engagement signals**: likes, comments, shares (estimated from source)
- **Framework match**: map to L1-L8 / V1-V6 from `framework/content-frameworks.md`
- **Hook analysis**: what makes the hook work (pattern interrupt, data shock, curiosity gap, etc.)
- **Virality driver**: why it went viral. Categories:
  - Relatability ("this is SO me")
  - Controversy / contrarian take
  - Data shock / surprising statistic
  - Emotional storytelling
  - Humor / meme format
  - Practical value / actionable tips
  - Identity validation ("I'm not the only one")
- **Adaptability score** (1-5): how easy it is to adapt to the brand
  - 5 = universal emotion/structure, zero brand-specific elements
  - 4 = easy swap of niche-specific details
  - 3 = requires some creative reframing
  - 2 = heavily tied to the original author's personal story
  - 1 = too personal/brand-specific, hard to adapt

**Filter out posts with adaptability score < 3.**

Rank remaining posts by: adaptability score (primary) + estimated engagement (secondary).

### Step 5 — Generate Adaptations
For each selected viral post (top 3-5 by count parameter), generate a full adaptation:

**5a) Adapted hook**
Rewrite the original hook in the brand's voice + target language. Keep the same psychological trigger (curiosity gap, pattern interrupt, data shock) but change the niche-specific elements.

**5b) Adapted structure**
Write the full post skeleton mapped to the brand's niche and personas:
- Replace the original niche/industry references with the brand's niche
- Replace the original audience with the brand's target persona
- Keep the emotional arc and structural rhythm identical
- Adapt examples, data points, and scenarios to the brand's world
- Apply the brand's tone (from tone-guide.md)
- Match the brand level (0-4) to the content pillars strategy

**5c) Key changes log**
Document what was changed and why, so the user understands the adaptation logic.

**5d) What to keep identical**
Document the structural/emotional elements that made it viral and MUST be preserved: hook pattern, paragraph rhythm, emotional arc, CTA style, etc.

### Step 6 — AI Detection Check
Apply `framework/ai-detection-signals.md` to all adapted text:
- [ ] No Tier 1/Tier 2 red-flag words (delve, leverage, seamless, robust, etc.)?
- [ ] No AI-typical opening phrases ("In today's fast-paced world", "Let's dive in", etc.)?
- [ ] Sentence length varies (mix short 3-7 words and long 20+ words, not all 12-18)?
- [ ] Paragraph lengths vary (not all the same size)?
- [ ] Uses contractions naturally (it's, can't, don't)?
- [ ] Includes at least one specific/concrete detail (not generic)?
- [ ] No relentless positivity — includes honest/critical perspective where appropriate?
- [ ] No formulaic structure (not everything grouped in 3s, not perfectly symmetrical)?
- [ ] Avoids em dash overuse?
- [ ] Passes the "would a human say this to a friend?" test?

Fix any issues before presenting.

### Step 7 — Present Results
Format showing side-by-side: original viral post vs adapted version for the brand.

```
## Viral Remix — [Brand]

**Niche**: [searched niche]
**Markets searched**: [US, FR, ES, ...]
**Platform**: [LinkedIn/TikTok/Instagram]
**Format**: [post/carousel/video]
**Date**: YYYY-MM-DD

---

### 1. [Adapted title] — Adaptability: [N]/5

**ORIGINAL**
> **Author**: [name] ([niche], [country])
> **Engagement**: ~[N]K likes, ~[N] comments
> **Framework**: [L7 — Contrarian Take]
> **Hook**: "[original opening line]"
> **Virality driver**: [why it worked]
> **Source**: [URL where found]

**ADAPTATION FOR [BRAND]**
> **Hook**: "[adapted opening line]"
> **Framework**: [L7]
> **Pillar**: [N — name]
> **Persona**: [target]
> **Brand level**: [0-4]

[FULL ADAPTED POST TEXT]

**What was kept**: [structural elements preserved]
**What was changed**: [niche-specific adaptations]

---

### 2. [Adapted title] — Adaptability: [N]/5
...
```

### Step 8 — Save & Offer Next Actions

**8a) Save to archive**
Save the remix report to `brands/[brand]/content-library/remixes/YYYY-MM/YYYY-MM-DD-remix-slug.md` with frontmatter:

```yaml
---
date: YYYY-MM-DD
type: viral-remix
original_source: "[URL or description]"
original_author: "[name]"
original_market: "[country]"
original_engagement: "[estimated metrics]"
original_framework: LN
adapted_framework: LN
pillar: N
persona: name
brand_level: N
topic: "description"
adaptability_score: N/5
status: draft
---
```

**8b) Offer next actions**
1. "Want me to polish one of these into a full post? Tell me the number and I'll use `/linkedin-post`"
2. "Want to search in a different market?"
3. "Want to search adjacent niches?"
4. "Want a video version? Tell me the number and I'll use `/video-script`"
5. "Want a carousel version? Tell me the number and I'll use `/carousel`"

## Invocation Examples
- `/viral-remix "AI recruiting"` — find viral posts about AI recruiting across multiple markets
- `/viral-remix "AI recruiting" --market US` — focus search on the US market
- `/viral-remix "remote work productivity" --count 3` — find top 3 viral posts on the topic
- `/viral-remix "employer branding" --market FR --market DE` — search French and German markets
- `/viral-remix "leadership mistakes" --format carousel` — find viral carousels on leadership
- `/viral-remix "content creation tools" --platform tiktok` — find viral TikTok content

## Important Notes
- This skill searches for **already proven** content. If research doesn't find viral posts with clear engagement signals, say so honestly rather than presenting mediocre results as "viral"
- Always credit the original author in the analysis (never plagiarize — the goal is to adapt the structure and angle, not copy the text)
- The adapted version should be different enough that it's clearly original content inspired by a proven format, not a translation or copy
- Prioritize adaptations that fit the brand's tone (from tone-guide.md) — a viral post that clashes with the brand's voice is not worth adapting
- **AI detection**: all adapted text must avoid AI red-flag words and patterns from `framework/ai-detection-signals.md`
- If the user asks to polish a specific remix, pass the full adapted text as context to the relevant skill (`/linkedin-post`, `/video-script`, or `/carousel`)
