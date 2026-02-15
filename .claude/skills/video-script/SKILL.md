---
name: video-script
description: Generate a video script for the active brand (Reels, TikTok, YouTube). Use when the user wants to create a video.
user-invocable: true
argument-hint: [topic] [--pillar N] [--framework VN] [--platform reels|tiktok] [--speaker name]
allowed-tools: Read, Write, Glob, Grep, WebSearch, WebFetch
---

# Skill: Generate Video Script

## Instructions

When the user invokes `/video-script`, generate a complete video script for the active brand following this workflow.

**Default active brand**: ai-social-media-manager (`brands/ai-social-media-manager/`). For other brands, specify `--brand [name]`.

### Step 1 — Load Context
ALWAYS read these files from the active brand before generating any content:
- `brands/[brand]/brand-voice.md` — voice, identity, golden rules
- `brands/[brand]/audience-personas.md` — target personas
- `brands/[brand]/tone-guide.md` (or `tono-infotainment.md` for legacy brands) — tone, humor, linguistic patterns, video style

### Step 2 — Online Research on the Topic
Before generating the script, search for fresh data and inspiration:

**2a) Recent data and statistics**
Use `WebSearch` to find up-to-date data on the topic:
- Reports and statistics from authoritative sources
- Recent academic research or surveys on the topic
- Market-specific data where possible

**2b) Viral videos on the same topic**
Use `WebSearch` to find:
- Viral Reels/TikTok on the same subject
- Formats and hooks that generated engagement
- Trending audio and popular formats in the niche

**2c) Research synthesis**
Summarize findings into:
- 1-3 data points/statistics with source (to use in the script)
- 1-2 original angles from the research
- Patterns from viral videos (hooks, formats, duration, style)

**Note**: if research doesn't produce relevant results, proceed with generation based on sector knowledge.

### Step 3 — Parse Arguments
The user provides a topic (required) and optionally:
- `--pillar N` (1-5): select the content pillar. Default: auto
- `--framework VN` (V1-V6): select the video framework. Default: auto
- `--platform reels|tiktok`: target platform. Default: reels
- `--speaker name`: who speaks in the video. Default: auto (based on brand config)

If needed, also read:
- `brands/[brand]/content-pillars.md` — for the pillar
- `framework/content-frameworks.md` — for the framework
- `framework/video-playbook.md` — for templates and technical specs
- `brands/[brand]/framework-examples.md` — for brand-specific examples

### Step 3b — Detect Language
Determine the language for the script:
1. Read the `Language:` field from the brand's `brand-voice.md`
2. If specified, use that language without asking
3. If not specified, detect the language of the conversation
4. If the user is speaking a language different from English and no brand language is set, ask: "I notice you're speaking [language]. Should I generate this script in [language]?"

### Step 4 — Generate the Complete Script
The script must include ALL 5 levels for each time segment. Write all dialogue and on-screen text in the language determined in Step 3b:

```
[TIMESTAMP]
VISUAL: what's on screen (framing, expressions, props, graphics)
AUDIO: exact word-for-word dialogue + tone indication
ON-SCREEN TEXT: overlay text + position
DIRECTION: editing notes (cut, zoom, transition, pacing)
MUSIC/SFX: background audio, sound effects
```

Incorporate data and insights from online research (Step 2) where relevant.

### Step 5 — Verify the Hook
The hook in the first 2-3 seconds MUST:
- Be a pattern interrupt (visual OR verbal OR text)
- Create an "open loop" that the viewer wants to close
- Work EVEN without audio (text + visual only)
- Make the viewer think "wait, what did they say?" or "oh god, that's me"

If the hook doesn't pass this test, rewrite it before proceeding.

### Step 6 — Verify the Tone
The video must:
- Make the target smile/recognize themselves
- Provide value (insight, data, advice)
- Not be a brand ad (unless it's a BOFU pillar)
- Use humor about the SITUATION, never about the person
- Follow the emotional structure: Frustration → Escalation → Payoff
- Have accurate data/statistics with source

### Step 7 — Present the Script
Present the finished script with these metadata:

```
## Video Script — [Brand]

**Platform**: Reels / TikTok
**Estimated duration**: XX seconds
**Speaker**: [name]
**Pillar**: [number and name]
**Framework**: [code and name]
**Target persona**: [name]
**Brand level**: [0-4]
**Production difficulty**: Low / Medium / High
**Research sources**: [list of sources used]

---

[COMPLETE SCRIPT WITH ALL 5 LEVELS]

---

**Production notes**: [location, props needed, graphics to prepare]
**Cross-platform adaptation**: [notes for adapting to Reels/TikTok if different]
```

### Step 8 — Save to Archive
Save the script to `brands/[brand]/content-library/video/YYYY-MM/YYYY-MM-DD-slug.md` with frontmatter:

```yaml
---
date: YYYY-MM-DD
platform: reels|tiktok
duration_seconds: N
speaker: name
pillar: N
framework: VN
persona: name
brand_level: N
topic: "short description"
production_difficulty: low|medium|high
sources: []
status: draft
---
```

### Step 9 — Offer Options
After presentation, offer:
1. "Want a version for [other platform]?"
2. "Want a companion LinkedIn post? Use `/linkedin-post`"
3. "Want a variation with a different hook?"
4. "Want a carousel version? Use `/carousel`"

## Invocation Examples
- `/video-script "content creation workflow"` — generate a Reels script with auto framework and pillar
- `/video-script "the CEO wants 5 candidates by tomorrow" --framework V6 --platform tiktok` — infotainment sketch for TikTok
- `/video-script "3 screening mistakes" --framework V4` — mini-lesson
- `/video-script "keyword matching vs AI reasoning" --framework V2 --pillar 4` — split screen comparison

## Important Notes
- The AUDIO text must be the EXACT dialogue, word for word, not a summary
- Facial expressions are crucial: specify them for every segment
- The script must work EVEN without audio (visual + on-screen text only)
- Target duration: 15-30 seconds for Reels, 15-45 for TikTok
- Every video must have subtitles planned in the safe zone
