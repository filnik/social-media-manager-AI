---
name: content-ideas
description: Find and suggest content ideas for the active brand by analyzing the market. Use when the user wants to find inspiration, trends, or ideas for new social content.
user-invocable: true
argument-hint: [topic] [--trending]
allowed-tools: Read, Write, Glob, Grep, WebSearch, WebFetch
---

# Skill: Find Content Ideas

## Instructions

When the user invokes `/content-ideas`, search for and suggest content ideas for the active brand by analyzing the market. Supports general research and newsjacking mode with `--trending`.

**Default active brand**: ai-social-media-manager (`brands/ai-social-media-manager/`). For other brands, specify `--brand [name]`.

### Step 1 — Load Context
ALWAYS read these files from the active brand before searching for ideas:
- `brands/[brand]/brand-voice.md` — voice, identity, golden rules
- `brands/[brand]/content-pillars.md` — pillars and editorial calendar
- `framework/content-frameworks.md` — frameworks L1-L8 (LinkedIn) + V1-V6 (Video)
- `brands/[brand]/audience-personas.md` — target personas
- `brands/[brand]/tone-guide.md` (or `tono-infotainment.md` for legacy brands) — tone, humor, linguistic patterns

### Step 2 — Parse Arguments
The user can provide:
- **Topic** (optional): subject to search ideas for (e.g., "AI Act", "remote interviews")
- **`--trending`** (optional): activates newsjacking mode (trends and recent news)

Possible combinations:
- `/content-ideas` — general market scan for the brand's niche
- `/content-ideas "AI Act"` — ideas on a specific topic
- `/content-ideas --trending` — current trends in the brand's sector
- `/content-ideas --trending "EU directive"` — trends on a specific topic

### Step 3 — Market Research (standard mode)
If `--trending` is NOT active, run these searches:

**3a) Viral content in the brand's niche (international)**
Use `WebSearch` to find:
- Viral LinkedIn posts in the brand's sector
- TikTok/Reels trends in the niche
- Industry newsletters and publications
- If a specific topic is given, focus queries on it

**3b) Viral content in the brand's niche (local market)**
Use `WebSearch` to find:
- Local-market LinkedIn posts in the brand's sector
- Articles and discussions in the brand's market
- Market-specific data and reports
- If a specific topic is given, focus queries on it

**3c) Winning patterns and formats**
Analyze results to identify:
- Hooks that worked (opening lines, pattern interrupts)
- Original angles on the same topic
- Formats that drive engagement (lists, stories, shocking data, comparisons)
- Tone and style of top-performing content

### Step 3-trending — Trend Research (newsjacking mode)
If `--trending` IS active, REPLACE standard Step 3 with:

**3a-trending) Recent news in the brand's sector**
Use `WebSearch` to find news from the last 7 days on:
- Key topics in the brand's niche
- Industry changes, regulations, trends
- AI, automation, and innovation in the sector
- If a specific topic is given, focus on it

**3b-trending) Ongoing social trends**
Use `WebSearch` to find:
- Trending LinkedIn hashtags in the niche
- Viral TikTok/Reels topics in the sector
- Viral discussions on Twitter/X about the niche
- Viral memes or formats adaptable to the brand's sector

**3c-trending) Newsjacking evaluation**
For each news/trend found, evaluate:
- **Timeliness**: is it still fresh? (<48h ideal, <7 days acceptable)
- **Relevance**: does it naturally connect to the brand's sector?
- **Humor potential**: does it lend itself to the brand's tone?
- **Reputational risk**: is there a risk of seeming opportunistic or insensitive?

Discard trends with high reputational risk or low relevance.

### Step 3d — Detect Language
Determine the language for the output:
1. Read the `Language:` field from the brand's `brand-voice.md`
2. If specified, use that language without asking
3. If not specified, detect the language of the conversation
4. Present ideas and hooks in the detected/specified language

### Step 4 — Map to Brand Frameworks
For each idea found, map to:
- **Pillar**: which content pillar it belongs to
- **Framework**: which framework fits best (L1-L8 for LinkedIn, V1-V6 for video)
- **Persona**: which target persona
- **Format**: LinkedIn post, Reels video, TikTok video, carousel
- **Brand level** (0-4): how present the brand is in the content

### Step 5 — Verify Originality
For each idea:
- Check `brands/[brand]/content-library/` to verify it hasn't already been covered
- Verify it fits the brand's tone (as defined in the tone guide)
- Verify it follows the "hero is the reader, not the brand" rule
- Discard duplicate or overly similar ideas to already published content

### Step 6 — Present Ideas
Present up to 10 ideas, ordered by priority (urgency for trending, viral potential for standard).

**Standard format:**

```
## Content Ideas — [Brand]

**Mode**: General scan / Trending
**Topic**: [topic if specified, otherwise "general"]
**Research date**: YYYY-MM-DD

---

### 1. [Idea title]
**Concept**: [description in 2-3 lines]
**Suggested hook**: "[opening line]"
**Why it works**: [1-2 lines]
**Inspiration source**: [what inspired the idea]
**Pillar**: [N] | **Framework**: [LN/VN] | **Persona**: [name] | **Format**: [type]
**Brand level**: [0-4]

---

### 2. [Idea title]
...
```

**Additional fields for trending ideas (only with `--trending`):**

```
**TRENDING**: [reference news/trend]
**Time window**: [when to publish by, e.g., "within 48h", "by end of week"]
**Newsjacking angle**: [how to connect the trend to the brand's world]
```

### Step 7 — Offer Actions
After presentation, offer:
1. "Want me to generate a LinkedIn post from an idea? Tell me the number and I'll use `/linkedin-post`"
2. "Want me to generate a video script from an idea? Tell me the number and I'll use `/video-script`"
3. "Want me to generate a carousel from an idea? Tell me the number and I'll use `/carousel`"
4. "Want to dive deeper into a specific topic?"
5. "Want me to search for trends with `--trending`?" (only if not already active)

## Invocation Examples
- `/content-ideas` — general market scan for the brand's niche
- `/content-ideas "AI Act"` — ideas on a specific topic
- `/content-ideas --trending` — current trends for newsjacking
- `/content-ideas --trending "EU directive"` — trends on a specific topic

## Important Notes
- Online searches don't always produce relevant results: in that case, generate ideas based on sector knowledge and the brand's frameworks
- Prioritize ideas that fit the brand's tone (as defined in the tone guide)
- For trending ideas, timeliness is key: a good idea published now beats a perfect idea published late
- Never suggest content that could be perceived as insensitive or opportunistic
