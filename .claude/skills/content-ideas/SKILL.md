---
name: content-ideas
description: Cerca e suggerisce idee per contenuti del brand attivo analizzando il mercato. Usa quando l'utente vuole trovare spunti, trend o idee per nuovi contenuti social.
user-invocable: true
argument-hint: [tema] [--trending]
allowed-tools: Read, Write, Glob, Grep, WebSearch, WebFetch
---

# Skill: Cerca Idee Contenuti

## Istruzioni

Quando l'utente invoca `/content-ideas`, cerca e suggerisce idee per contenuti social del brand attivo analizzando il mercato. Supporta ricerca generale e modalita' newsjacking con `--trending`.

**Brand attivo di default**: Mastrohr (`brands/mastrohr/`). Per altri brand, specifica `--brand [nome]`.

### Step 1 — Carica il Contesto
Leggi SEMPRE questi file del brand attivo prima di cercare idee:
- `brands/[brand]/brand-voice.md` — voce, identita', regole d'oro
- `brands/[brand]/content-pillars.md` — i pillar e il calendario editoriale
- `framework/content-frameworks.md` — framework L1-L8 (LinkedIn) + V1-V6 (Video)
- `brands/[brand]/audience-personas.md` — le personas target
- `brands/[brand]/tono-infotainment.md` — tono, ironia, pattern linguistici

### Step 2 — Parsa gli Argomenti
L'utente puo' fornire:
- **Tema** (opzionale): argomento su cui cercare idee (es. "AI Act", "colloqui da remoto")
- **`--trending`** (opzionale): attiva la modalita' newsjacking (trend e notizie recenti)

Combinazioni possibili:
- `/content-ideas` — scansione generale mercato HR-tech
- `/content-ideas "AI Act"` — idee su un tema specifico
- `/content-ideas --trending` — trend attuali HR/lavoro
- `/content-ideas --trending "direttiva UE"` — trend su un tema specifico

### Step 3 — Ricerca di Mercato (modalita' standard)
Se `--trending` NON e' attivo, esegui queste ricerche:

**3a) Contenuti virali HR-tech USA**
Usa `WebSearch` per cercare:
- Contenuti LinkedIn virali su HR, recruiting, talent acquisition (USA)
- Trend TikTok/Reels HR e recruiting
- Newsletter HR (HR Brew, People Managing People, TLNT, SHRM)
- Se c'e' un tema specifico, focalizza le query su quello

**3b) Contenuti virali HR-tech Italia**
Usa `WebSearch` per cercare:
- Post LinkedIn virali HR Italia
- Articoli e discussioni su lavoro/recruiting in Italia
- Dati ISTAT, INPS, Osservatorio Politecnico su lavoro/HR
- Se c'e' un tema specifico, focalizza le query su quello

**3c) Pattern e formati vincenti**
Analizza i risultati per identificare:
- Hook che hanno funzionato (frasi di apertura, pattern interrupt)
- Angoli originali sullo stesso topic
- Formati che generano engagement (liste, storie, dati shock, confronti)
- Tono e stile dei contenuti piu' performanti

### Step 3-trending — Ricerca Trend (modalita' newsjacking)
Se `--trending` E' attivo, SOSTITUISCI lo Step 3 standard con:

**3a-trending) Notizie recenti HR/lavoro Italia**
Usa `WebSearch` per cercare notizie degli ultimi 7 giorni su:
- Lavoro, occupazione, disoccupazione in Italia
- HR, recruiting, selezione del personale
- AI nel lavoro, automazione, nuove normative
- Se c'e' un tema specifico, focalizza su quello

**3b-trending) Trend social in corso**
Usa `WebSearch` per cercare:
- Hashtag LinkedIn trending su HR/lavoro
- Topic virali TikTok/Reels su lavoro e recruiting
- Discussioni virali su Twitter/X riguardo lavoro in Italia
- Meme o format virali adattabili al mondo HR

**3c-trending) Valutazione newsjacking**
Per ogni notizia/trend trovato, valuta:
- **Tempestivita'**: e' ancora fresco? (<48h ideale, <7 giorni accettabile)
- **Rilevanza HR**: si collega naturalmente al mondo HR/recruiting?
- **Potenziale ironico**: si presta al tono infotainment Mastrohr?
- **Rischio reputazionale**: c'e' rischio di sembrare opportunistici o insensibili?

Scarta i trend con alto rischio reputazionale o bassa rilevanza HR.

### Step 4 — Mappa sui Framework Mastrohr
Per ogni idea trovata, mappa su:
- **Pillar** (1-5): a quale content pillar appartiene
- **Framework**: quale framework e' piu' adatto (L1-L8 per LinkedIn, V1-V6 per video)
- **Persona**: quale persona target (Francesca, Marco, Sara)
- **Formato**: post LinkedIn, video Reels, video TikTok, carosello
- **Livello Mastrohr** (0-4): quanto Mastrohr e' presente nel contenuto

### Step 5 — Verifica Originalita'
Per ogni idea:
- Controlla `brands/[brand]/content-library/` per verificare che non sia gia' stata trattata
- Verifica che sia adattabile al tono infotainment (autorevole + ironico + empatico)
- Verifica che rispetti la regola "l'eroe e' l'HR, non Mastrohr"
- Scarta le idee duplicate o troppo simili a contenuti gia' pubblicati

### Step 6 — Presenta le Idee
Presenta massimo 10 idee, ordinate per priorita' (urgenza per trending, potenziale virale per standard).

**Formato standard:**

```
## Idee Contenuti [Brand]

**Modalita'**: Scansione generale / Trending
**Tema**: [tema se specificato, altrimenti "generale"]
**Data ricerca**: YYYY-MM-DD

---

### 1. [Titolo idea]
**Concept**: [descrizione in 2-3 righe]
**Hook suggerito**: "[frase di apertura]"
**Perche' funziona**: [1-2 righe]
**Fonte ispirazione**: [cosa ha ispirato l'idea]
**Pillar**: [N] | **Framework**: [LN/VN] | **Persona**: [nome] | **Formato**: [tipo]
**Livello Mastrohr**: [0-4]

---

### 2. [Titolo idea]
...
```

**Campi aggiuntivi per idee trending (solo con `--trending`):**

```
**TRENDING**: [notizia/trend di riferimento]
**Finestra temporale**: [entro quando pubblicare, es. "entro 48h", "entro fine settimana"]
**Angolo newsjacking**: [come agganciare il trend al mondo HR/Mastrohr]
```

### Step 7 — Offri Azioni
Dopo la presentazione, offri:
1. "Vuoi che generi un post LinkedIn da un'idea? Dimmi il numero e uso `/linkedin-post`"
2. "Vuoi che generi uno script video da un'idea? Dimmi il numero e uso `/video-script`"
3. "Vuoi approfondire la ricerca su un tema specifico?"
4. "Vuoi che cerchi trend con `--trending`?" (solo se non era gia' attivo)

## Esempi di Invocazione
- `/content-ideas` — scansione generale mercato HR-tech
- `/content-ideas "AI Act"` — idee su un tema specifico
- `/content-ideas --trending` — trend attuali HR/lavoro per newsjacking
- `/content-ideas --trending "direttiva UE"` — trend su un tema specifico

## Note Importanti
- Le ricerche online possono non produrre sempre risultati rilevanti: in quel caso, genera idee basate sulla conoscenza del mercato HR e sui framework Mastrohr
- Privilegia idee che si prestano al tono infotainment (ironia + valore)
- Per le idee trending, la tempestivita' e' fondamentale: meglio un'idea buona pubblicata subito che un'idea perfetta pubblicata in ritardo
- Non suggerire mai contenuti che possano essere percepiti come insensibili o opportunistici
