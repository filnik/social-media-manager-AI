# AI Social Media Manager

## What is this project

Reusable framework for social content generation. Supports multiple brands simultaneously with shared knowledge base, experts, and frameworks.

**Committed demo brand**: `ai-social-media-manager` — the project itself, used as a demo of the multi-brand system.

**Private brand (not committed)**: `mastrohr` — Italian HR-tech startup (in `.gitignore`).

## Core rule

**Before generating ANY content** (post, video, carousel, text), ALWAYS read from the active brand:
1. `brands/[brand]/brand-voice.md` — voice and identity
2. `brands/[brand]/tone-guide.md` (or `tono-infotainment.md` for legacy brands) — tone and style
3. `brands/[brand]/audience-personas.md` — target personas

These 3 files are the DNA of every piece of brand content.

## Available skills

- `/linkedin-post [topic]` — generate a complete LinkedIn post for the active brand
- `/video-script [topic]` — generate a complete video script (Reels/TikTok/YouTube)
- `/carousel [topic]` — generate a LinkedIn carousel (PDF document post) for the active brand
- `/content-ideas [topic] [--trending]` — find and suggest content ideas by analyzing the market
- `/create-brand [brand-name]` — create the complete configuration for a new brand (from repo, slides, documents, or guided interview; competitors researched automatically)

## Language

**Documentation, frameworks, skills, and expert profiles** are always in English.

**Brand content** (posts, videos, carousels) is generated in the user's language:
- Default language: English
- If the user speaks a different language, ask for confirmation before switching: "I notice you're speaking [language]. Should I generate brand content in [language]?"
- If the brand's `brand-voice.md` has a `Language:` field, use that without asking
- Technical terms (hook, dwell time, engagement, CTA) remain in English regardless of language

## Key rules

1. **The hero is the customer**, never the brand. The brand emerges as a natural solution
2. **65% of content** doesn't name the brand. Only 10% is direct selling
3. **Humor about the situation**, never about the person
4. **Specific numbers** > generic claims
5. **Zero fluff**: no empty buzzwords, no exaggerated promises
6. **Never say "replaces"**: the brand frees, empowers, supports

## Project map

```
framework/                         # GENERIC — reusable for all brands
  content-frameworks.md            # Templates L1-L8 (LinkedIn) + V1-V6 (Video) + S1-S3
  linkedin-playbook.md             # LinkedIn rules
  video-playbook.md                # Video specs

experts/                           # GENERIC — 60 profiles with universal examples
  linkedin/                        # 6 experts (Welsh, Acosta, Alic, van der Blom, Turner, Queen)
  social-media/
    international/                 # 18 experts (Vaynerchuk, Godin, Miller, etc.)
    italian/                       # 11 experts (Montemagno, Diegoli, Gentili, etc.)
  youtube/
    international/                 # 15 experts (MrBeast, Ali Abdaal, etc.)
    italian/                       # 10 experts (Ascani, Bottoni, Taverniti, etc.)

brands/                            # SPECIFIC — one brand per directory
  ai-social-media-manager/         # Demo brand (committed)
    brand-voice.md                 # Voice and identity
    audience-personas.md           # Alex, Sara, Marco
    tone-guide.md                  # Tone guide
    content-pillars.md             # 4 pillars, editorial calendar
    framework-examples.md          # Generated content examples
    content-library/               # Content archive

.claude/skills/
  linkedin-post/SKILL.md           # /linkedin-post
  video-script/SKILL.md            # /video-script
  carousel/SKILL.md                # /carousel
  content-ideas/SKILL.md           # /content-ideas
  create-brand/SKILL.md            # /create-brand
```

### Mastrohr Brand (private — Italian)
The Mastrohr brand is an Italian HR-tech startup. All its files are in Italian and should NOT be translated. Key context:

**Personas**:
- **Francesca** — HR Director, SME (100-500 employees), drowning in CVs, wants to do strategy
- **Marco** — Startup CEO (20-100 employees), does recruiting alone, wants speed
- **Sara** — TA Specialist (200-1000 employees), 30 open roles, wants better tools

**Content Pillars**:
1. **Future of HR** (TOFU) — AI trends, data, regulations
2. **Hiring That Works** (MOFU) — best practices, mistakes, how-to
3. **HR in Chaos** (MOFU) — daily situations, humor, infotainment
4. **Behind the Scenes** (BRAND) — founders, startup, team

**Tone**: Infotainment — authoritative + ironic + empathetic + edgy. HR laughs AND learns.

**Founders**:
- **Marta Della Valle** — main video speaker, direct and empathetic tone
- **Michele Pavone** — tech speaker, explains AI accessibly
