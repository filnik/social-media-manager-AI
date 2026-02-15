---
name: linkedin-post
description: Generate a LinkedIn post for the active brand. Use when the user wants to create a LinkedIn post.
user-invocable: true
argument-hint: [topic] [--pillar N] [--framework LN] [--persona name]
allowed-tools: Read, Write, Glob, Grep, WebSearch, WebFetch
---

# Skill: Generate LinkedIn Post

## Instructions

When the user invokes `/linkedin-post`, generate a complete LinkedIn post for the active brand following this workflow.

**Default active brand**: ai-social-media-manager (`brands/ai-social-media-manager/`). For other brands, specify `--brand [name]`.

### Step 1 — Load Context
ALWAYS read these files from the active brand before generating any content:
- `brands/[brand]/brand-voice.md` — voice, identity, golden rules
- `brands/[brand]/audience-personas.md` — target personas
- `brands/[brand]/tone-guide.md` (or `tono-infotainment.md` for legacy brands) — tone, humor, linguistic patterns

### Step 2 — Online Research on the Topic
Before generating the post, search for fresh data and inspiration:

**2a) Recent data and statistics**
Use `WebSearch` to find up-to-date data on the topic:
- Reports and statistics from authoritative sources (McKinsey, Gartner, LinkedIn Economic Graph, etc.)
- Recent academic research or surveys on the topic
- Market-specific data where possible

**2b) Viral content on the same topic**
Use `WebSearch` to find:
- Viral LinkedIn posts on the same subject
- Angles and hooks that generated engagement
- How other creators in the same niche approach the topic

**2c) Research synthesis**
Summarize findings into:
- 1-3 data points/statistics with source (to use in the post)
- 1-2 original angles from the research
- Patterns from viral content (what works, what to avoid)

**Note**: if research doesn't produce relevant results, proceed with generation based on sector knowledge.

### Step 3 — Parse Arguments
The user provides a topic (required) and optionally:
- `--pillar N` (1-5): select the content pillar. If omitted, choose the most appropriate
- `--framework LN` (L1-L8): select the LinkedIn framework. If omitted, choose the best fit
- `--persona name`: target persona. Default: auto-select based on topic

If needed, also read:
- `brands/[brand]/content-pillars.md` — for the pillar
- `framework/content-frameworks.md` — for the framework
- `framework/linkedin-playbook.md` — for templates and rules
- `brands/[brand]/framework-examples.md` — for brand-specific examples

### Step 3b — Detect Language
Determine the language for the post:
1. Read the `Language:` field from the brand's `brand-voice.md`
2. If specified, use that language without asking
3. If not specified, detect the language of the conversation
4. If the user is speaking a language different from English and no brand language is set, ask: "I notice you're speaking [language]. Should I generate this post in [language]?"

### Step 4 — Generate the Post
Fill in the selected framework template with the provided topic. The post must:
1. Have a hook that captures in 140 characters (first line)
2. Provide genuine value even without mentioning the brand
3. Use the brand's tone as defined in the tone guide
4. Have the brand as an implicit solution (not the subject)
5. Include a natural CTA (question for comments or "link in comments")
6. Have 3-5 hashtags at the end
7. Be 800-1300 characters long
8. Be written in the language determined in Step 3b (technical terms in English where natural)
9. Incorporate data and insights from online research (Step 2) where relevant

### Step 5 — Verify with Checklist
Check every point from the checklist in `framework/linkedin-playbook.md`:
- [ ] Hook captures in 140 characters?
- [ ] Body provides genuine value?
- [ ] Brand voice is consistent?
- [ ] Tone matches the brand's guide?
- [ ] The hero is the reader (not the brand)?
- [ ] No links in the body?
- [ ] Short paragraphs?
- [ ] Max 3-5 hashtags at the end?
- [ ] Max 1-2 functional emojis?
- [ ] Natural CTA?
- [ ] 800-1300 characters?
- [ ] Data/statistics are accurate with source?

### Step 6 — Present the Post
Present the finished post with these metadata:

```
## LinkedIn Post — [Brand]

**Pillar**: [number and name]
**Framework**: [code and name]
**Target persona**: [name]
**Brand level**: [0-4]
**Funnel**: [TOFU/MOFU/BOFU]
**Research sources**: [list of sources used]

---

[COMPLETE POST]

---

**Characters**: [count]
**Notes**: [any notes on timing, context, variants]
```

### Step 7 — Save to Archive
Save the post to `brands/[brand]/content-library/linkedin/YYYY-MM/YYYY-MM-DD-slug.md` with frontmatter:

```yaml
---
date: YYYY-MM-DD
pillar: N
framework: LN
persona: name
brand_level: N
funnel: TOFU|MOFU|BOFU
topic: "short description"
sources: []
status: draft
---
```

### Step 8 — Offer Variations
After presentation, offer:
1. "Want a version with a different hook?"
2. "Want a video companion for this post? Use `/video-script`"
3. "Want a carousel version? Use `/carousel`"
4. "Want a version for a different persona?"

## Invocation Examples
- `/linkedin-post "CV screening with AI"` — generate a post on the topic with automatic pillar, framework, and persona
- `/linkedin-post "Monday morning HR frustrations" --pillar 3 --framework L8` — infotainment post with Shared Frustration
- `/linkedin-post "AI Act and recruiting" --pillar 1 --persona marco` — TOFU post for a CEO persona
- `/linkedin-post "SME case study 200 CVs" --framework L5` — narrative case study
