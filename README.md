# AI Social Media Manager

Framework open-source per generare contenuti social con [Claude Code](https://docs.anthropic.com/en/docs/claude-code).

60 profili esperti | 14 template | 4 skill automatizzate | Multi-brand

---

## Cosa fa

Trasforma Claude Code in un social media manager che conosce le strategie dei migliori content creator al mondo.

- **`/linkedin-post [topic]`** — Genera un post LinkedIn ottimizzato con hook, struttura, tono del tuo brand
- **`/video-script [topic]`** — Crea uno script video completo (Reels, TikTok, YouTube)
- **`/content-ideas [tema]`** — Trova idee per contenuti analizzando il mercato (con flag `--trending`)
- **`/create-brand [nome]`** — Configura un nuovo brand da zero con intervista guidata

Ogni contenuto generato e' personalizzato sulla voce del TUO brand, non generico.

---

## Quick Start

```bash
# 1. Clona il repo
git clone https://github.com/[username]/ai-social-media-manager.git
cd ai-social-media-manager

# 2. Apri con Claude Code
claude

# 3. Configura il tuo brand
/create-brand "il-tuo-brand"

# 4. Genera il tuo primo contenuto
/linkedin-post "un topic che ti interessa"
```

Il comando `/create-brand` ti guida passo passo: ti chiede tono, personas, pillar, competitor. Alla fine genera tutti i file di configurazione del brand.

---

## Come funziona

```
Tu scrivi: /linkedin-post "produttivita' nel lavoro remoto"

Il sistema:
1. Carica la brand voice del tuo brand (tono, stile, personalita')
2. Legge le audience personas (a chi stai parlando)
3. Consulta i 60 profili esperti per strategie e framework
4. Seleziona il template piu' adatto tra 14 disponibili
5. Cerca online dati e trend aggiornati
6. Genera il post con hook, struttura, CTA ottimizzati
7. Salva il contenuto nella content library del brand
```

La differenza rispetto a un prompt singolo: il sistema **conosce** il tuo brand, il tuo target e le strategie che funzionano. Non genera contenuti generici — genera contenuti **tuoi**.

---

## Struttura del progetto

```
framework/                         # Generico — riutilizzabile per tutti i brand
  content-frameworks.md            # Template L1-L8 (LinkedIn) + V1-V6 (Video) + S1-S3
  linkedin-playbook.md             # Regole LinkedIn (algoritmo, orari, hashtag)
  video-playbook.md                # Specifiche video (hook, retention, formati)

experts/                           # 60 profili esperti con framework e tecniche
  linkedin/                        # 6 esperti LinkedIn strategy
  social-media/
    internazionali/                # 18 esperti content & social media
    italiani/                      # 11 esperti digital marketing italiano
  youtube/
    internazionali/                # 15 esperti YouTube & video
    italiani/                      # 10 esperti YouTube italiano

brands/                            # Un brand per directory
  ai-social-media-manager/         # Brand di esempio (questo progetto)
    brand-voice.md                 # Voce e identita'
    audience-personas.md           # Le personas target
    tono-infotainment.md           # Guida al tono
    content-pillars.md             # Pillar e calendario editoriale
    framework-examples.md          # Esempi di contenuti generati
    content-library/               # Archivio contenuti

.claude/skills/                    # Le 4 skill automatizzate
  linkedin-post/SKILL.md
  video-script/SKILL.md
  content-ideas/SKILL.md
  create-brand/SKILL.md
```

---

## I 60 esperti

Ogni profilo contiene: bio, filosofia, framework dettagliati, tecniche di hook, citazioni, risorse. Non sono riassunti — sono guide approfondite con esempi applicabili.

### LinkedIn Strategy (6)
| Esperto | Specialita' |
|---------|-------------|
| Justin Welsh | Personal brand, Content Operating System, solopreneur |
| Lara Acosta | Storytelling, framework SLAY, vulnerabilita' |
| Jasmin Alic | Hook e re-hook, copywriting persuasivo |
| Richard van der Blom | Dati algoritmo LinkedIn, performance formati |
| Lea Turner | Storytelling autentico, engagement organico |
| Tim Queen | Carousel mastery, B2B content strategy |

### Social Media — Internazionali (18)
| Esperto | Specialita' |
|---------|-------------|
| Gary Vaynerchuk | Content model, Day Trading Attention, Jab/Hook |
| Seth Godin | Smallest Viable Audience, Permission Marketing |
| Donald Miller | StoryBrand, storytelling strutturato |
| Ann Handley | Writing, Utility x Inspiration x Empathy |
| Brendan Kane | Hook Point, primi 3 secondi |
| Neil Patel | SEO, content marketing data-driven |
| Chris Walker | Dark Social, ALLBOUND |
| Rand Fishkin | Zero-Click Marketing, Amplifier Audience |
| David Perell | Writing online, Personal Monopoly |
| Jay Baer | Youtility, Talk Triggers |
| Joe Pulizzi | Content Inc., content-first business |
| Russell Brunson | Funnel, storytelling di vendita |
| Amy Porterfield | Digital courses, list building |
| Mark Schaefer | KNOWN, personal branding |
| Brian Dean | SEO copywriting, Skyscraper Technique |
| Julia McCoy | AI content, Content at Scale |
| Michael Stelzner | Social Media Examiner, industry analysis |
| Tim Hughes | Social selling, Smarketing |

### Social Media — Italiani (11)
| Esperto | Specialita' |
|---------|-------------|
| Marco Montemagno | Video content, imprenditorialita' digitale |
| Gianluca Diegoli | Marketing connesso, strategia digitale |
| Veronica Gentili | Facebook/IG ads, #FuffaFree |
| Dario Vignali | Marketers community, personal branding |
| Riccardo Scandellari | Personal branding, Rock'n'Blog |
| Luca La Mesa | Social media strategy, real-time marketing |
| Mirko Pallera | Marketing non-convenzionale, DNA virale |
| Chiara Dosio | Funnel organico, content strategy |
| Rudy Bandiera | Digital communication, personal brand |
| Francesca Anzalone | Comunicazione digitale, crisis management |
| Alessio Beltrami | Content marketing, blogging aziendale |

### YouTube — Internazionali (15)
| Esperto | Specialita' |
|---------|-------------|
| MrBeast | Retention, thumbnail, scaling |
| Ali Abdaal | Produttivita', creator business |
| Sean Cannell | YouTube growth, Think Media |
| Paddy Galloway | Analisi canali, strategia YouTube |
| Jenny Hoyos | Shorts, micro-content virale |
| Colin & Samir | Creator economy, storytelling |
| Pat Flynn | Community, passive income |
| Derral Eves | Algoritmo YouTube, optimization |
| Jake Thomas | Thumbnail, titoli, CTR |
| Roberto Blake | Creator economy, diversificazione |
| Nick Nimmin | YouTube growth per piccoli canali |
| Tim Schmoyer | Community building, Video Creators |
| Vanessa Lau | Personal brand su YouTube |
| Film Booth | Cinematografia, storytelling visivo |
| Sunny Lenarduzzi | YouTube per business, Authority Accelerator |

### YouTube — Italiani (10)
| Esperto | Specialita' |
|---------|-------------|
| Marcello Ascani | Vlogging, imprenditorialita' |
| Andrea Bottoni | YouTube growth, strategia |
| Giorgio Taverniti | SEO YouTube, community |
| Dario Vignali | Business online, corsi |
| Luca Mastella | YouTube growth, analisi |
| Slim Dogs | Produzione video, storytelling |
| Giovanni Perilli | YouTube SEO, ottimizzazione |
| Casa Surace | Viral comedy, storytelling regionale |
| Luca Mazzucchelli | Psicologia, video educativi |
| Daniele Doesn't Matter | Commentary, storytelling |

---

## I 14 template

### LinkedIn (L1-L8)
| Template | Tipo | Quando usarlo |
|----------|------|---------------|
| L1 | Il Dato Sorprendente | Hai una statistica che sfida le aspettative |
| L2 | La Storia del Cliente | Racconto di un risultato concreto |
| L3 | Il Post Educativo | Lista di consigli, errori, lezioni |
| L4 | Il Contrarian | Opinione che va contro il consenso |
| L5 | Il Meme Professionale | Situazione riconoscibile + ironia |
| L6 | Il Post Fondatore | Storia personale + progetto |
| L7 | Il Prima/Dopo | Trasformazione misurabile |
| L8 | La Domanda Provocatoria | Domanda che genera discussione |

### Video (V1-V6)
| Template | Tipo | Quando usarlo |
|----------|------|---------------|
| V1 | POV Situazionale | "POV: sei un [ruolo] e..." |
| V2 | Il Dato + Sketch | Dato reale + mini-sketch |
| V3 | Il Tutorial Veloce | How-to in 30-60 secondi |
| V4 | Il Conflitto tra Ruoli | Dialogo tra due figure professionali |
| V5 | Il Reaction | Reazione a trend/notizia |
| V6 | Il Dietro le Quinte | Behind the scenes autentico |

### Strategici (S1-S3)
| Template | Tipo | Quando usarlo |
|----------|------|---------------|
| S1 | Content Pyramid | Da 1 contenuto lungo a 10+ micro-contenuti |
| S2 | Jab Jab Hook | Pianificare il mix valore/vendita |
| S3 | Calendar Builder | Generare un calendario editoriale |

---

## Multi-brand

Il framework supporta piu' brand contemporaneamente. Ogni brand ha la sua directory in `brands/` con configurazione indipendente.

```bash
# Genera un post per il brand default
/linkedin-post "topic"

# Genera un post per un brand specifico
/linkedin-post "topic" --brand nome-brand
```

Per aggiungere un nuovo brand:
```bash
/create-brand "nome-del-brand"
```

Il sistema ti intervista su: identita', tono di voce, audience personas, content pillar, competitor. Poi genera automaticamente tutti i file di configurazione.

---

## Requisiti

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installato
- Un account Anthropic con accesso a Claude

---

## Contribuire

Contribuzioni benvenute. Alcune idee:

- **Nuovi esperti**: Aggiungi profili nella directory `experts/` seguendo il formato esistente
- **Nuovi template**: Estendi i framework in `framework/content-frameworks.md`
- **Nuove skill**: Crea nuove skill in `.claude/skills/`
- **Miglioramenti**: Bug fix, documentazione, ottimizzazioni

Ogni profilo esperto deve:
- Essere generico (usare `[il tuo brand]`, non brand specifici)
- Contenere: profilo, filosofia, framework dettagliati, tecniche di hook, citazioni, risorse
- Seguire il formato dei profili esistenti

---

## License

MIT — vedi [LICENSE](LICENSE)
