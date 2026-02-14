# AI Social Media Manager

## Cos'e' questo progetto

Framework riutilizzabile per generazione contenuti social. Supporta piu' brand contemporaneamente con knowledge base, esperti e framework condivisi.

**Brand di esempio committato**: `ai-social-media-manager` — il progetto stesso, usato come demo del sistema multi-brand.

**Brand privato (non committato)**: `mastrohr` — startup HR-tech italiana (in `.gitignore`).

## Regola fondamentale

**Prima di generare QUALSIASI contenuto** (post, video, testo), leggi SEMPRE dal brand attivo:
1. `brands/[brand]/brand-voice.md` — voce e identita'
2. `brands/[brand]/tono-infotainment.md` — tono e stile
3. `brands/[brand]/audience-personas.md` — le personas target

Questi 3 file sono il DNA di ogni contenuto del brand.

## Skills disponibili

- `/linkedin-post [topic]` — genera un post LinkedIn completo per il brand attivo
- `/video-script [topic]` — genera uno script video completo (Reels/TikTok/YouTube)
- `/content-ideas [tema] [--trending]` — cerca e suggerisce idee per contenuti analizzando il mercato
- `/create-brand [nome-brand]` — crea la configurazione completa per un nuovo brand

## Lingua

**Solo italiano.** Termini tecnici inglesi dove naturale nel settore.

## Regole chiave

1. **L'eroe e' il cliente**, mai il brand. Il brand emerge come soluzione naturale
2. **65% dei contenuti** non nomina il brand. Solo 10% e' vendita diretta
3. **Ironia sulla situazione**, mai sulla persona
4. **Numeri specifici** > affermazioni generiche
5. **Zero fuffa**: niente buzzword vuoti, niente promesse esagerate
6. **Mai dire "sostituisce"**: il brand libera, potenzia, supporta

## Mappa del progetto

```
framework/                         # GENERICO — riutilizzabile per tutti i brand
  content-frameworks.md            # Template L1-L8 (LinkedIn) + V1-V6 (Video) + S1-S3
  linkedin-playbook.md             # Regole LinkedIn
  video-playbook.md                # Specifiche video

experts/                           # GENERICO — 60 profili con esempi universali
  linkedin/                        # 6 esperti (Welsh, Acosta, Alic, van der Blom, Turner, Queen)
  social-media/
    internazionali/                # 18 esperti (Vaynerchuk, Godin, Miller, etc.)
    italiani/                      # 11 esperti (Montemagno, Diegoli, Gentili, etc.)
  youtube/
    internazionali/                # 15 esperti (MrBeast, Ali Abdaal, etc.)
    italiani/                      # 10 esperti (Ascani, Bottoni, Taverniti, etc.)

brands/                            # SPECIFICO — un brand per directory
  ai-social-media-manager/         # Brand di esempio (committato)
    brand-voice.md                 # Voce e identita'
    audience-personas.md           # Alex, Sara, Marco
    tono-infotainment.md           # Guida al tono
    content-pillars.md             # 4 pillar, calendario editoriale
    framework-examples.md          # Esempi di contenuti generati
    content-library/               # Archivio contenuti

.claude/skills/
  linkedin-post/SKILL.md           # /linkedin-post
  video-script/SKILL.md            # /video-script
  content-ideas/SKILL.md           # /content-ideas
  create-brand/SKILL.md            # /create-brand
```

### Personas
- **Francesca** — HR Director PMI (100-500 dip.), sommersa di CV, vuole fare strategia
- **Marco** — CEO Startup (20-100 dip.), fa recruiting da solo, vuole velocita'
- **Sara** — TA Specialist (200-1000 dip.), 30 ruoli aperti, vuole tool migliori

### Content Pillar
1. **Futuro dell'HR** (TOFU) — trend AI, dati, normative
2. **Selezione che Funziona** (MOFU) — best practice, errori, how-to
3. **L'HR nel Caos** (MOFU) — situazioni quotidiane, ironia, infotainment
5. **Dietro le Quinte** (BRAND) — fondatori, startup, team

### Tono
**Infotainment**: autorevole + ironico + empatico + pungente. L'HR ride E impara.

### Fondatori
- **Marta Della Valle** — speaker principale video, tono diretto ed empatico
- **Michele Pavone** — speaker tecnico, spiega AI in modo accessibile
