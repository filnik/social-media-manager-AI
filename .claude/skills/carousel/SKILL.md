---
name: carousel
description: Genera un carousel LinkedIn (PDF document post) per il brand attivo. Usa quando l'utente vuole creare un carousel o trasformare un post esistente in carousel.
user-invocable: true
argument-hint: [topic or "from post [slug]"] [--slides N] [--persona name]
allowed-tools: Read, Write, Glob, Grep, WebSearch, WebFetch
---

# Skill: Generate LinkedIn Carousel

## Instructions

When the user invokes `/carousel`, generate a complete LinkedIn carousel (document post) for the active brand following this workflow.

**Default active brand**: ai-social-media-manager (`brands/ai-social-media-manager/`). For other brands, specify `--brand [name]`.

### Step 1 — Load Context
ALWAYS read these files from the active brand before generating any content:
- `brands/[brand]/brand-voice.md` — voice, identity, golden rules
- `brands/[brand]/audience-personas.md` — target personas
- `brands/[brand]/tone-guide.md` (or `tono-infotainment.md`) — tone, humor, linguistic patterns

Also read:
- `framework/linkedin-playbook.md` — carousel strategy section and LinkedIn rules
- `brands/[brand]/content-pillars.md` — content pillars

### Step 2 — Determine Input Mode
The carousel can be created in two ways:

**Mode A — From a topic (default)**
The user provides a topic. Proceed to Step 3 for online research, then generate the carousel.

**Mode B — From an existing LinkedIn post**
The user specifies `from post [slug]` or pastes an existing post. Read the post from `brands/[brand]/content-library/linkedin/` and transform it into a carousel format. Skip Step 3 (research) since the content already exists.

### Step 3 — Online Research (Mode A only)
Before generating the carousel, search for fresh data and inspiration:

**3a) Recent data and statistics**
Use `WebSearch` to find up-to-date data on the topic:
- Reports and statistics from authoritative sources
- Recent surveys and studies on the topic
- Industry-specific data where possible

**3b) Viral carousels on the same topic**
Use `WebSearch` to find:
- Viral LinkedIn carousels on the same or similar topics
- Angles and hooks that generated engagement
- Visual and structural patterns that work

**3c) Research synthesis**
Summarize findings into:
- 1-3 data points/statistics with source (to use in the carousel)
- 1-2 original angles from the research
- Patterns from viral carousels (what works, what to avoid)

**Note**: if research doesn't produce relevant results, proceed with generation based on sector knowledge.

### Step 4 — Parse Arguments
The user provides a topic (required) and optionally:
- `--slides N` (4-10): number of slides. Default: 6
- `--persona name`: target persona. Default: auto-select
- `--pillar N`: content pillar. Default: auto-select

### Step 5 — Generate Carousel Content
Create the carousel following this structure:

**Slide 1 — Cover (The Hook)**
- Bold headline that stops the scroll (max 8-10 words)
- Subtitle with value promise (what the reader will learn)
- Author name/handle and brand logo
- Must work as a standalone image in the feed

**Slide 2 — The Problem / Context**
- State the problem, frustration, or situation the audience recognizes
- Use a specific data point if available
- Create the "open loop" that makes people keep swiping

**Slides 3-N-1 — The Content (Key Points)**
Each content slide should have:
- **Tagline**: short label at top (e.g., "Mistake #1", "Step 2", "The Data")
- **Title**: one clear idea per slide (max 6-8 words)
- **Body**: 2-3 short sentences explaining the point
- **Visual note**: suggested icon, graphic, or visual element

Rules for content slides:
- ONE idea per slide — no exceptions
- Short, scannable text (max 40 words per slide)
- Build logically: each slide flows into the next
- Use numbers, data, and specifics over vague claims
- Alternate between data slides, insight slides, and actionable slides

**Slide N — CTA (The Close)**
- Recap the key takeaway in one sentence
- Clear CTA: follow, comment, save, share, or "link in comments"
- Author name/handle and brand logo
- Optional: teaser for related content

### Step 6 — Write the Companion Caption
Write the LinkedIn caption that accompanies the carousel:
- 2-4 sentences that complement (not repeat) the carousel content
- Include a question to drive comments
- "Link in comments" if applicable
- 3-5 hashtags at the end

### Step 7 — Verify Quality
Check every point:
- [ ] Cover slide hooks in <3 seconds?
- [ ] One clear idea per slide?
- [ ] Max 40 words per slide?
- [ ] Logical flow from slide to slide?
- [ ] Data/statistics are accurate with source?
- [ ] Brand voice is consistent?
- [ ] CTA is clear and natural?
- [ ] 4-10 slides total?
- [ ] Caption is ready?
- [ ] The hero is the reader, not the brand?

### Step 8 — Present the Carousel
Present the finished carousel with these metadata:

```
## LinkedIn Carousel — [Brand]

**Topic**: [topic]
**Slides**: [count]
**Pillar**: [number and name]
**Persona target**: [name]
**Brand level**: [0-4]
**Funnel**: [TOFU/MOFU/BOFU]
**Research sources**: [list of sources used]

---

### Slide 1 — Cover
**Headline**: [headline text]
**Subtitle**: [subtitle text]
**Visual**: [description of visual elements]

### Slide 2 — [Tagline]
**Title**: [title]
**Body**: [body text]
**Visual**: [description]

### Slide 3 — [Tagline]
...

### Slide N — CTA
**Headline**: [key takeaway]
**CTA**: [call to action]
**Visual**: [description]

---

## Caption

[Caption text with hashtags]

---

**Total slides**: [count]
**Notes**: [production notes, timing, variants]
```

### Step 9 — Visual Generation Instructions
After presenting the content, provide instructions for visual generation:

1. **Using aicarousels.com**: Go to https://www.aicarousels.com, paste the slide content, select a template matching the brand style, and download as PDF
2. **Manual PDF creation**: Use Canva, Figma, or Google Slides with 1080x1350px slides (4:5 ratio for LinkedIn), export as PDF
3. **Key visual guidelines**:
   - Consistent color scheme across all slides
   - Large, readable fonts (min 24pt for body, 36pt+ for titles)
   - Plenty of white space
   - Brand colors and logo on first and last slide
   - Use icons/illustrations sparingly — clarity over decoration

### Step 10 — Save to Archive
Save the carousel in `brands/[brand]/content-library/linkedin/YYYY-MM/YYYY-MM-DD-carousel-slug.md` with frontmatter:

```yaml
---
date: YYYY-MM-DD
type: carousel
slides: N
pillar: N
persona: name
brand_level: N
funnel: TOFU|MOFU|BOFU
topic: "short description"
sources: []
status: draft
---
```

### Step 11 — Offer Variations
After presentation, offer:
1. "Want a version with a different hook?"
2. "Want a LinkedIn text post on the same topic? Use `/linkedin-post`"
3. "Want a video companion? Use `/video-script`"
4. "Want to adjust the number of slides?"

## Language Behavior
- Read the `Language:` field from the brand's `brand-voice.md`
- If not specified, use the language of the conversation
- Generate all carousel content in the detected/specified language
- If the user is speaking a language different from the brand's configured language, ask for confirmation before switching

## Invocation Examples
- `/carousel "5 mistakes in content marketing"` — generate a 6-slide carousel on the topic
- `/carousel "AI trends 2026" --slides 8` — generate an 8-slide carousel
- `/carousel from post 2026-02-10-screening-ai` — transform existing post into carousel
- `/carousel "lead generation" --persona marco --pillar 2` — targeted carousel

## Important Notes
- LinkedIn carousels are uploaded as PDF documents (document posts)
- Optimal ratio: 4:5 (1080x1350px) or 1:1 (1080x1080px). 4:5 takes more feed space
- Carousels get ~6.1% avg engagement rate — higher than most other formats
- Sweet spot: 6-10 slides. Engagement drops after 10+ slides
- The first slide IS the thumbnail in the feed — it must hook on its own
- Each slide must be self-contained enough to make sense if screenshotted
- Document posts increase dwell time, which LinkedIn's algorithm rewards heavily
