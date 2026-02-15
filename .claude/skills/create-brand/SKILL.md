---
name: create-brand
description: Create the complete configuration for a new brand. Can extract info automatically from a repo, slides, or documents, or run a guided interview. Researches competitors automatically. Generates all necessary files in brands/[brand-name]/.
user-invocable: true
argument-hint: [brand-name]
allowed-tools: Read, Write, Glob, Grep, WebSearch, WebFetch
---

# Skill: Create New Brand

## Instructions

When the user invokes `/create-brand [brand-name]`, start the onboarding process for a new brand following this workflow:

### Step 1 — Check Prerequisites
1. Check that `brands/[brand-name]/` doesn't already exist. If it does, warn the user and ask if they want to overwrite.
2. Read `framework/content-frameworks.md` to have the available templates (L1-L8, V1-V6, S1-S3).
3. Read an existing brand (e.g., `brands/ai-social-media-manager/brand-voice.md`) as a reference for the expected format and quality.

### Step 1b — Determine Input Mode
The brand can be created in 3 ways:

**Mode A — From documents/sources (automatic)**
If the user provides source material (repo with code, slides, PDF, presentation documents, website), automatically extract all possible information:
- Read the provided files (code, README, slides, docs) with `Read`
- If it's a website, use `WebFetch` to extract info
- Derive: name, what it does, differentiator, sector, tone, target audience
- Proceed directly to Step 3b for confirmation, skipping interviews
- Only ask the user for what you can't infer from the materials

**Mode B — Guided interview (interactive)**
If the user doesn't provide material, start the interview (Steps 2-4).

**Mode C — Hybrid**
The user provides partial material + answers specific questions for missing info.

Ask the user which mode they prefer, or infer it from context (e.g., if they say "create a brand from my repo", use Mode A).

### Step 2 — Interview: Brand Identity
*(Only if Mode B or C — skip if info was already extracted from documents)*

Ask the user (using `AskUserQuestion` where possible):

- **Brand name** and tagline (if they have one)
- **What the product/service does** (short description, 1-2 sentences)
- **Key differentiator** compared to competitors (the unique selling proposition)
- **Sector** and target market (B2B/B2C, geographic area, target company size)
- **Founders/speakers** (who will be the faces of the brand in content — name, role, tone)

### Step 3 — Interview: Audience and Tone
*(Only if Mode B or C — skip if info was already extracted from documents)*

Ask the user:

- **Personas** (2-4): for each, ask for role, age, main frustrations, goals, language used
- **Desired tone**: propose a scale on 3 axes:
  - Formal ↔ Informal
  - Serious ↔ Humorous
  - Technical ↔ Accessible
- If the user doesn't know, suggest combinations based on the sector (e.g., "For a B2B SaaS, I'd recommend: informal + slightly humorous + accessible")
- **Priority platforms** (LinkedIn, Instagram, TikTok, YouTube — order by priority)

### Step 3b — Confirm Extracted Info (Mode A only)
If you extracted info from documents, present a summary:
- What I understood about the brand (name, product, differentiator, sector)
- Personas I'm proposing (based on inferred target)
- Tone I'm proposing (based on analyzed material)
- Ask for confirmation: "Does this look right? Want to change anything?"

### Step 4 — Competitor Research (automatic)
**Do NOT ask the user for competitors.** Search for them autonomously:

1. Use `WebSearch` to find competitors in the brand's sector:
   - "[sector] competitor [target market]"
   - "[product type] alternatives"
   - "best [category] [market]"
2. Identify 3-6 relevant competitors
3. For each competitor, gather with `WebSearch` and `WebFetch`:
   - What they do, positioning, pricing
   - How they communicate on social (tone, frequency, platforms)
   - Strengths and weaknesses in content marketing
4. If the user mentions specific competitors, include them and add others from research
5. Present the found competitors to the user for confirmation

### Step 4b — Content Strategy
Define (proposing sensible defaults based on sector and competitors):

- **Content pillars** (3-5): main themes around which content revolves. Propose based on sector, competitors, and positioning
- **Funnel**: how to distribute content between TOFU (awareness) / MOFU (consideration) / BOFU (conversion). Propose the S1 distribution (30/40/20/10) as default
- **Brand level** in content: how present the brand should be
  - 0 = never named (65% of content)
  - 1 = implicit
  - 2 = mentioned
  - 3 = case study
  - 4 = direct selling (max 10% of content)
- **References**: brands they admire for tone, creators they follow, content they'd like to emulate

### Step 4c — Detect Language
Before generating brand files, detect the language the user is speaking:

1. If the user is speaking English, set brand language to English (no confirmation needed)
2. If the user is speaking a different language (e.g., Italian, Spanish, French), ask: "I see you're speaking [language]. Should brand content be generated in [language]?"
3. Save the confirmed language in `brand-voice.md` as a `Language:` field at the top of the file
4. All brand files (brand-voice, personas, tone-guide, content-pillars, framework-examples) will be written in the confirmed language

### Step 5 — Generate Brand Files
With all collected info, create `brands/[brand-name]/` with this structure:

| File | Content |
|------|---------|
| `brand-voice.md` | Identity, voice, applied StoryBrand (hero = customer, guide = brand), golden rules, do/don't |
| `content-pillars.md` | The 3-5 pillars with: description, tone, target personas, frequency, funnel position, recommended frameworks |
| `audience-personas.md` | Detailed profiles of 2-4 personas: fictional name, role, age, frustrations, goals, language, how they find content, what convinces them |
| `tone-guide.md` | Brand-specific tone guide: linguistic patterns, words to use, words to avoid, examples of right vs wrong tone |
| `expert-applications.md` | File with header and empty template — ready for future expert applications to the brand |
| `framework-examples.md` | 2-3 compiled framework examples using the new brand (at minimum one L1 or L4 + one V1 or V6) |
| `competitors/README.md` | Competitor list with brief description and positioning relative to the brand |
| `content-library/linkedin/.gitkeep` | Directory ready for LinkedIn content |
| `content-library/video/instagram/.gitkeep` | Directory ready for Reels |
| `content-library/video/tiktok/.gitkeep` | Directory ready for TikTok |
| `content-library/video/youtube/.gitkeep` | Directory ready for YouTube |

**File format**: use the same style and structure as files in `brands/ai-social-media-manager/` as reference.

### Step 6 — Present and Validate
1. Show a summary of everything created:
   - Number of files generated
   - Personas defined
   - Pillars chosen
   - Platforms configured
2. Show a preview of the generated `brand-voice.md`
3. Ask for user confirmation: "All good? Want to change anything?"
4. If the user confirms, suggest next steps:
   - "Want to generate a first piece of content? Use `/linkedin-post [topic]`"
   - "Want to generate a video script? Use `/video-script [topic]`"
   - "Want to find content ideas? Use `/content-ideas [topic]`"

## Important Notes

- **Language**: brand files are written in the language confirmed in Step 4c. Framework and documentation files are always in English.
- **Quality**: generated files must be complete and operational, not placeholders. The brand should be able to start generating content immediately after setup.
- **StoryBrand**: always apply Donald Miller's framework — the hero is the customer, the brand is the guide.
- **Competitors**: ALWAYS search for competitors automatically with `WebSearch`. Don't ask the user to list them — find them yourself and ask for confirmation.
- **Input from documents**: when the user provides source material (repo, slides, PDF, website), extract as much as possible and only ask for missing info. The goal is to minimize questions.
- **Flexibility**: not all questions are mandatory. If the user doesn't know how to answer something, propose sensible defaults based on the sector.

## Invocation Examples

- `/create-brand "acme-saas"` — start the interactive onboarding for the brand "acme-saas"
- `/create-brand "acme-saas"` + "here's the repo: github.com/acme/saas" — extract info from the repo and create the brand automatically
- `/create-brand "acme-saas"` + "here are the presentation slides" — extract info from slides
- `/create-brand "green-energy"` + "here's our website: green-energy.com" — analyze the website and create the brand
- `/create-brand "rossi-law-firm"` — set up a brand for a law firm (guided interview)
