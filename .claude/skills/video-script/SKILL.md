---
name: video-script
description: Genera script e sceneggiatura video per il brand attivo (Reels, TikTok, YouTube). Usa quando l'utente vuole creare un video.
user-invocable: true
argument-hint: [topic] [--pillar N] [--framework VN] [--platform reels|tiktok] [--speaker marta|michele]
allowed-tools: Read, Write, Glob, Grep, WebSearch, WebFetch
---

# Skill: Genera Script Video

## Istruzioni

Quando l'utente invoca `/video-script`, genera uno script video completo per il brand attivo seguendo questo workflow.

**Brand attivo di default**: Mastrohr (`brands/mastrohr/`). Per altri brand, specifica `--brand [nome]`.

### Step 1 — Carica il Contesto
Leggi SEMPRE questi file del brand attivo prima di generare qualsiasi contenuto:
- `brands/[brand]/brand-voice.md` — voce, identita', regole d'oro
- `brands/[brand]/audience-personas.md` — le personas target
- `brands/[brand]/tono-infotainment.md` — tono, ironia, pattern linguistici, stile video

### Step 2 — Ricerca Online sul Topic
Prima di generare lo script, cerca dati freschi e ispirazione online:

**2a) Dati e statistiche recenti**
Usa `WebSearch` per cercare dati aggiornati sul topic:
- Report e statistiche (ISTAT, Eurostat, McKinsey, Randstad, LinkedIn Economic Graph)
- Ricerche accademiche o survey recenti sul tema
- Dati specifici per il mercato italiano dove possibile

**2b) Video virali sullo stesso topic**
Usa `WebSearch` per cercare:
- Video Reels/TikTok virali su HR, recruiting, lavoro (USA e Italia)
- Format e hook video che hanno generato engagement
- Trend audio e format popolari nel settore HR/lavoro

**2c) Sintesi ricerca**
Sintetizza i risultati in:
- 1-3 dati/statistiche con fonte (da usare nello script)
- 1-2 angoli originali emersi dalla ricerca
- Pattern dai video virali (hook, format, durata, stile)

**Nota**: se la ricerca non produce risultati rilevanti, procedi comunque con la generazione basandoti sulla conoscenza del settore.

### Step 3 — Parsa gli Argomenti
L'utente fornisce un topic (obbligatorio) e opzionalmente:
- `--pillar N` (1-5): seleziona il content pillar. Default: auto
- `--framework VN` (V1-V6): seleziona il framework video. Default: auto (V6 se infotainment, V3 se dato, V4 se how-to)
- `--platform reels|tiktok`: piattaforma target. Default: reels
- `--speaker marta|michele`: chi parla nel video. Default: marta

Se serve, leggi anche:
- `brands/[brand]/content-pillars.md` — per il pillar
- `framework/content-frameworks.md` — per il framework
- `framework/video-playbook.md` — per i template e le specifiche tecniche
- `brands/[brand]/framework-examples.md` — per esempi specifici del brand

### Step 4 — Genera lo Script Completo
Lo script deve includere TUTTI i 5 livelli per ogni segmento temporale:

```
[TIMESTAMP]
VISUAL: cosa si vede (inquadratura, espressioni, props, grafiche)
AUDIO: dialogo esatto parola per parola + indicazione di tono
ON-SCREEN TEXT: testo sovrapposto + posizione
REGIA: note di montaggio (taglio, zoom, transizione, ritmo)
MUSICA/SFX: audio di sottofondo, effetti sonori
```

Incorporare dati e insight dalla ricerca online (Step 2) dove rilevanti.

### Step 5 — Verifica l'Hook
L'hook nei primi 2-3 secondi DEVE:
- Essere un pattern interrupt (visivo O verbale O testuale)
- Creare un "loop aperto" che il viewer vuole chiudere
- Funzionare ANCHE senza audio (solo testo + visual)
- Far dire al viewer "aspetta, cos'ha detto?" oppure "oddio, sono io"

Se l'hook non supera questo test, riscrivilo prima di procedere.

### Step 6 — Verifica il Tono Infotainment
Il video deve:
- Far sorridere/riconoscere il target
- Dare valore (insight, dato, consiglio)
- Non essere una pubblicita' di Mastrohr (a meno che sia Pillar 4)
- Usare ironia sulla SITUAZIONE, mai sulla persona
- Avere la struttura emotiva: Frustrazione → Escalation → Payoff
- Dati/statistiche accurati e con fonte

### Step 7 — Presenta lo Script
Presenta lo script finito con questi metadati:

```
## Script Video [Brand]

**Piattaforma**: Reels / TikTok
**Durata stimata**: XX secondi
**Speaker**: Marta / Michele
**Pillar**: [numero e nome]
**Framework**: [codice e nome]
**Persona target**: [nome]
**Livello Mastrohr**: [0-4]
**Difficolta' produzione**: Bassa / Media / Alta
**Fonti ricerca**: [elenco fonti usate nella ricerca online]

---

[SCRIPT COMPLETO CON TUTTI I 5 LIVELLI]

---

**Note di produzione**: [location, props necessari, grafiche da preparare]
**Adattamento cross-platform**: [note per adattare a Reels/TikTok se diverso]
```

### Step 8 — Salva nell'Archivio
Salva lo script in `brands/[brand]/content-library/video/YYYY-MM/YYYY-MM-DD-slug.md` con frontmatter:

```yaml
---
date: YYYY-MM-DD
platform: reels|tiktok
duration_seconds: N
speaker: marta|michele
pillar: N
framework: VN
persona: nome
livello_mastrohr: N
topic: "descrizione breve"
production_difficulty: low|medium|high
fonti: []
status: draft
---
```

### Step 9 — Offri Opzioni
Dopo la presentazione, offri:
1. "Vuoi una versione per [altra piattaforma]?"
2. "Vuoi un post LinkedIn companion? Usa `/linkedin-post`"
3. "Vuoi una variazione con hook diverso?"
4. "Vuoi la versione con Michele come speaker?"

## Esempi di Invocazione
- `/video-script "screening 200 CV nel 2026"` — genera script Reels con Marta, framework e pillar automatici
- `/video-script "il CEO vuole 5 candidati per domani" --framework V6 --platform tiktok` — sketch infotainment per TikTok
- `/video-script "3 errori di screening" --framework V4 --speaker michele` — mini-lezione con Michele
- `/video-script "keyword matching vs AI reasoning" --framework V2 --pillar 4` — confronto split screen
- `/video-script "dato ISTAT occupazione" --framework V3` — dato bomba con reazione

## Note Importanti
- Il testo AUDIO deve essere il dialogo ESATTO, parola per parola, non un riassunto
- Le espressioni facciali sono fondamentali: specificarle per ogni segmento
- Lo script deve funzionare anche SENZA audio (solo visual + on-screen text)
- La durata target e' 15-30 secondi per Reels, 15-45 per TikTok
- Ogni video deve avere i sottotitoli pianificati nella safe zone
