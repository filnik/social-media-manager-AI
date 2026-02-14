---
name: linkedin-post
description: Genera post LinkedIn per il brand attivo. Usa quando l'utente vuole creare un post LinkedIn.
user-invocable: true
argument-hint: [topic] [--pillar N] [--framework LN] [--persona nome]
allowed-tools: Read, Write, Glob, Grep, WebSearch, WebFetch
---

# Skill: Genera Post LinkedIn

## Istruzioni

Quando l'utente invoca `/linkedin-post`, genera un post LinkedIn completo per il brand attivo seguendo questo workflow.

**Brand attivo di default**: Mastrohr (`brands/mastrohr/`). Per altri brand, specifica `--brand [nome]`.

### Step 1 — Carica il Contesto
Leggi SEMPRE questi file del brand attivo prima di generare qualsiasi contenuto:
- `brands/[brand]/brand-voice.md` — voce, identita', regole d'oro
- `brands/[brand]/audience-personas.md` — le personas target
- `brands/[brand]/tono-infotainment.md` — tono, ironia, pattern linguistici

### Step 2 — Ricerca Online sul Topic
Prima di generare il post, cerca dati freschi e ispirazione online:

**2a) Dati e statistiche recenti**
Usa `WebSearch` per cercare dati aggiornati sul topic:
- Report e statistiche (ISTAT, Eurostat, McKinsey, Randstad, LinkedIn Economic Graph)
- Ricerche accademiche o survey recenti sul tema
- Dati specifici per il mercato italiano dove possibile

**2b) Contenuti virali sullo stesso topic**
Usa `WebSearch` per cercare:
- Post LinkedIn virali (USA e Italia) sullo stesso argomento
- Angoli e hook che hanno generato engagement
- Come altri creator HR trattano lo stesso tema

**2c) Sintesi ricerca**
Sintetizza i risultati in:
- 1-3 dati/statistiche con fonte (da usare nel post)
- 1-2 angoli originali emersi dalla ricerca
- Pattern dai contenuti virali (cosa funziona, cosa evitare)

**Nota**: se la ricerca non produce risultati rilevanti, procedi comunque con la generazione basandoti sulla conoscenza del settore.

### Step 3 — Parsa gli Argomenti
L'utente fornisce un topic (obbligatorio) e opzionalmente:
- `--pillar N` (1-5): seleziona il content pillar. Se omesso, scegli quello piu' appropriato
- `--framework LN` (L1-L8): seleziona il framework LinkedIn. Se omesso, scegli il piu' adatto
- `--persona nome` (francesca/marco/sara): target persona. Default: francesca

Se serve, leggi anche:
- `brands/[brand]/content-pillars.md` — per il pillar
- `framework/content-frameworks.md` — per il framework
- `framework/linkedin-playbook.md` — per i template e le regole
- `brands/[brand]/framework-examples.md` — per esempi specifici del brand

### Step 4 — Genera il Post
Compila il template del framework selezionato con il topic fornito. Il post deve:
1. Avere un hook che cattura in 140 caratteri (prima riga)
2. Dare valore genuino anche senza menzionare Mastrohr
3. Usare il tono infotainment: autorevole + ironico + empatico
4. Avere Mastrohr come soluzione implicita (non il soggetto)
5. Includere una CTA naturale (domanda per commenti o "link nei commenti")
6. Avere 3-5 hashtag alla fine
7. Essere lungo 800-1300 caratteri
8. Essere interamente in italiano (termini tecnici inglesi dove naturale)
9. Incorporare dati e insight dalla ricerca online (Step 2) dove rilevanti

### Step 5 — Verifica con Checklist
Controlla ogni punto della checklist in `framework/linkedin-playbook.md`:
- [ ] Hook cattura in 140 caratteri?
- [ ] Body da' valore genuino?
- [ ] Brand voice coerente?
- [ ] Tono infotainment?
- [ ] L'eroe e' l'HR (non Mastrohr)?
- [ ] Nessun link nel body?
- [ ] Paragrafi brevi?
- [ ] Max 3-5 hashtag alla fine?
- [ ] Max 1-2 emoji funzionali?
- [ ] CTA naturale?
- [ ] 800-1300 caratteri?
- [ ] Dati/statistiche accurati e con fonte?

### Step 6 — Presenta il Post
Presenta il post finito con questi metadati:

```
## Post LinkedIn [Brand]

**Pillar**: [numero e nome]
**Framework**: [codice e nome]
**Persona target**: [nome]
**Livello Mastrohr**: [0-4]
**Funnel**: [TOFU/MOFU/BOFU]
**Fonti ricerca**: [elenco fonti usate nella ricerca online]

---

[POST COMPLETO]

---

**Caratteri**: [conteggio]
**Note**: [eventuali note su timing, contesto, varianti]
```

### Step 7 — Salva nell'Archivio
Salva il post in `brands/[brand]/content-library/linkedin/YYYY-MM/YYYY-MM-DD-slug.md` con frontmatter:

```yaml
---
date: YYYY-MM-DD
pillar: N
framework: LN
persona: nome
livello_mastrohr: N
funnel: TOFU|MOFU|BOFU
topic: "descrizione breve"
fonti: []
status: draft
---
```

### Step 8 — Offri Variazioni
Dopo la presentazione, offri:
1. "Vuoi una versione con hook diverso?"
2. "Vuoi un video companion per questo post? Usa `/video-script`"
3. "Vuoi una versione per una persona diversa?"

## Esempi di Invocazione
- `/linkedin-post "screening CV con AI"` — genera un post sul topic con pillar, framework e persona automatici
- `/linkedin-post "frustrazioni HR lunedi' mattina" --pillar 3 --framework L8` — post infotainment con Frustrazione Condivisa
- `/linkedin-post "AI Act e recruiting" --pillar 1 --persona marco` — post TOFU per CEO
- `/linkedin-post "case study PMI 200 CV" --framework L5` — case study narrativo
