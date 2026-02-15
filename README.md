# AI Social Media Manager

Open-source framework to generate social content with [Claude Code](https://docs.anthropic.com/en/docs/claude-code).

60 expert profiles | 14 templates | 5 automated skills | Multi-brand

---

## What it does

Turns Claude Code into a social media manager that knows the strategies of the best content creators in the world.

- **`/linkedin-post [topic]`** — Generate an optimized LinkedIn post with hook, structure, and your brand's tone
- **`/video-script [topic]`** — Create a complete video script (Reels, TikTok, YouTube)
- **`/carousel [topic]`** — Generate a LinkedIn carousel (PDF document post) with structured slides
- **`/content-ideas [topic]`** — Find content ideas by analyzing the market (with `--trending` flag)
- **`/create-brand [name]`** — Set up a new brand from scratch: from a repo, slides, documents, or with a guided interview

Every piece of content is personalized to YOUR brand's voice, not generic.

---

## Quick Start

```bash
# 1. Clone the repo
git clone https://github.com/AlessandroFilworworworino/ai-social-media-manager.git
cd ai-social-media-manager

# 2. Open with Claude Code
claude

# 3. Set up your brand
/create-brand "your-brand"

# 4. Generate your first content
/linkedin-post "a topic you care about"
```

The `/create-brand` command works in 3 modes:
- **From documents**: pass it a repo, slides, PDF, or website and it creates the brand automatically
- **Guided interview**: it asks you about tone, personas, pillars step by step
- **Hybrid**: extracts what it can from materials and only asks for missing info

Competitors are researched automatically by the AI — you don't need to know them.

---

## How it works

```
You type: /linkedin-post "remote work productivity"

The system:
1. Loads your brand voice (tone, style, personality)
2. Reads your audience personas (who you're talking to)
3. Consults 60 expert profiles for strategies and frameworks
4. Selects the best-fitting template from 14 available
5. Searches online for fresh data and trends
6. Generates the post with optimized hook, structure, and CTA
7. Saves the content to the brand's content library
```

The difference from a single prompt: the system **knows** your brand, your target, and the strategies that work. It doesn't generate generic content — it generates content that's **yours**.

---

## Project structure

```
framework/                         # Generic — reusable for all brands
  content-frameworks.md            # Templates L1-L8 (LinkedIn) + V1-V6 (Video) + S1-S3
  linkedin-playbook.md             # LinkedIn rules (algorithm, timing, hashtags)
  video-playbook.md                # Video specs (hooks, retention, formats)

experts/                           # 60 expert profiles with frameworks and techniques
  linkedin/                        # 6 LinkedIn strategy experts
  social-media/
    international/                 # 18 content & social media experts
    italian/                       # 11 Italian digital marketing experts
  youtube/
    international/                 # 15 YouTube & video experts
    italian/                       # 10 Italian YouTube experts

brands/                            # One brand per directory
  ai-social-media-manager/         # Demo brand (this project)
    brand-voice.md                 # Voice and identity
    audience-personas.md           # Target personas
    tone-guide.md                  # Tone guide
    content-pillars.md             # Pillars and editorial calendar
    framework-examples.md          # Generated content examples
    content-library/               # Content archive

.claude/skills/                    # The 5 automated skills
  linkedin-post/SKILL.md
  video-script/SKILL.md
  carousel/SKILL.md
  content-ideas/SKILL.md
  create-brand/SKILL.md
```

---

## The 60 experts

Each profile contains: bio, philosophy, detailed frameworks, hook techniques, quotes, resources. These aren't summaries — they're in-depth guides with actionable examples.

### LinkedIn Strategy (6)
| Expert | Specialty |
|--------|-----------|
| Justin Welsh | Personal brand, Content Operating System, solopreneur |
| Lara Acosta | Storytelling, SLAY framework, vulnerability |
| Jasmin Alic | Hooks and re-hooks, persuasive copywriting |
| Richard van der Blom | LinkedIn algorithm data, format performance |
| Lea Turner | Authentic storytelling, organic engagement |
| Tim Queen | Carousel mastery, B2B content strategy |

### Social Media — International (18)
| Expert | Specialty |
|--------|-----------|
| Gary Vaynerchuk | Content model, Day Trading Attention, Jab/Hook |
| Seth Godin | Smallest Viable Audience, Permission Marketing |
| Donald Miller | StoryBrand, structured storytelling |
| Ann Handley | Writing, Utility x Inspiration x Empathy |
| Brendan Kane | Hook Point, first 3 seconds |
| Neil Patel | SEO, data-driven content marketing |
| Chris Walker | Dark Social, ALLBOUND |
| Rand Fishkin | Zero-Click Marketing, Amplifier Audience |
| David Perell | Writing online, Personal Monopoly |
| Jay Baer | Youtility, Talk Triggers |
| Joe Pulizzi | Content Inc., content-first business |
| Russell Brunson | Funnels, sales storytelling |
| Amy Porterfield | Digital courses, list building |
| Mark Schaefer | KNOWN, personal branding |
| Brian Dean | SEO copywriting, Skyscraper Technique |
| Julia McCoy | AI content, Content at Scale |
| Michael Stelzner | Social Media Examiner, industry analysis |
| Tim Hughes | Social selling, Smarketing |

### Social Media — Italian (11)
| Expert | Specialty |
|--------|-----------|
| Marco Montemagno | Video content, digital entrepreneurship |
| Gianluca Diegoli | Connected marketing, digital strategy |
| Veronica Gentili | Facebook/IG ads, #FuffaFree |
| Dario Vignali | Marketers community, personal branding |
| Riccardo Scandellari | Personal branding, Rock'n'Blog |
| Luca La Mesa | Social media strategy, real-time marketing |
| Mirko Pallera | Unconventional marketing, viral DNA |
| Chiara Dosio | Organic funnels, content strategy |
| Rudy Bandiera | Digital communication, personal brand |
| Francesca Anzalone | Digital communication, crisis management |
| Alessio Beltrami | Content marketing, business blogging |

### YouTube — International (15)
| Expert | Specialty |
|--------|-----------|
| MrBeast | Retention, thumbnails, scaling |
| Ali Abdaal | Productivity, creator business |
| Sean Cannell | YouTube growth, Think Media |
| Paddy Galloway | Channel analysis, YouTube strategy |
| Jenny Hoyos | Shorts, viral micro-content |
| Colin & Samir | Creator economy, storytelling |
| Pat Flynn | Community, passive income |
| Derral Eves | YouTube algorithm, optimization |
| Jake Thomas | Thumbnails, titles, CTR |
| Roberto Blake | Creator economy, diversification |
| Nick Nimmin | YouTube growth for small channels |
| Tim Schmoyer | Community building, Video Creators |
| Vanessa Lau | Personal brand on YouTube |
| Film Booth | Cinematography, visual storytelling |
| Sunny Lenarduzzi | YouTube for business, Authority Accelerator |

### YouTube — Italian (10)
| Expert | Specialty |
|--------|-----------|
| Marcello Ascani | Vlogging, entrepreneurship |
| Andrea Bottoni | YouTube growth, strategy |
| Giorgio Taverniti | YouTube SEO, community |
| Dario Vignali | Online business, courses |
| Luca Mastella | YouTube growth, analysis |
| Slim Dogs | Video production, storytelling |
| Giovanni Perilli | YouTube SEO, optimization |
| Casa Surace | Viral comedy, regional storytelling |
| Luca Mazzucchelli | Psychology, educational videos |
| Daniele Doesn't Matter | Commentary, storytelling |

---

## The 14 templates

### LinkedIn (L1-L8)
| Template | Type | When to use |
|----------|------|-------------|
| L1 | The Surprising Data | You have a statistic that challenges expectations |
| L2 | The Client Story | A concrete result story |
| L3 | The Educational Post | List of tips, mistakes, lessons |
| L4 | The Contrarian | An opinion that goes against consensus |
| L5 | The Professional Meme | Relatable situation + humor |
| L6 | The Founder Post | Personal story + project |
| L7 | The Before/After | Measurable transformation |
| L8 | The Provocative Question | A question that sparks discussion |

### Video (V1-V6)
| Template | Type | When to use |
|----------|------|-------------|
| V1 | POV Situational | "POV: you're a [role] and..." |
| V2 | Data + Sketch | Real data + mini-sketch |
| V3 | Quick Tutorial | How-to in 30-60 seconds |
| V4 | Role Conflict | Dialogue between two professional figures |
| V5 | The Reaction | Reaction to a trend/news |
| V6 | Behind the Scenes | Authentic behind the scenes |

### Strategic (S1-S3)
| Template | Type | When to use |
|----------|------|-------------|
| S1 | Content Pyramid | From 1 long-form piece to 10+ micro-content |
| S2 | Jab Jab Hook | Plan the value/sales mix |
| S3 | Calendar Builder | Generate an editorial calendar |

---

## Multi-brand

The framework supports multiple brands simultaneously. Each brand has its own directory in `brands/` with independent configuration.

```bash
# Generate a post for the default brand
/linkedin-post "topic"

# Generate a post for a specific brand
/linkedin-post "topic" --brand brand-name
```

To add a new brand:
```bash
# Guided interview
/create-brand "your-brand-name"

# From a repository (extracts info from code and README)
/create-brand "your-brand-name"
> "here's the repo: github.com/org/repo"

# From slides or documents (extracts info automatically)
/create-brand "your-brand-name"
> "use the slides at /path/to/presentation.pdf"

# From a website
/create-brand "your-brand-name"
> "analyze the site: example.com"
```

The system extracts as much as possible from the provided sources, researches competitors automatically, and only asks for info it can't infer.

---

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed
- An Anthropic account with access to Claude

---

## Contributing

Contributions welcome. Some ideas:

- **New experts**: Add profiles in the `experts/` directory following the existing format
- **New templates**: Extend the frameworks in `framework/content-frameworks.md`
- **New skills**: Create new skills in `.claude/skills/`
- **Improvements**: Bug fixes, documentation, optimizations

Each expert profile should:
- Be generic (use `[your brand]`, not specific brand names)
- Contain: profile, philosophy, detailed frameworks, hook techniques, quotes, resources
- Follow the format of existing profiles

---

## License

MIT — see [LICENSE](LICENSE)
