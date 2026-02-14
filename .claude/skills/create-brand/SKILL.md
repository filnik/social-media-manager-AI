---
name: create-brand
description: Crea la configurazione completa per un nuovo brand. Puo' estrarre info automaticamente da repo, slide o documenti, oppure intervistare l'utente. Ricerca competitor in automatico. Genera tutti i file necessari in brands/[nome-brand]/.
user-invocable: true
argument-hint: [nome-brand]
allowed-tools: Read, Write, Glob, Grep, WebSearch, WebFetch
---

# Skill: Crea Nuovo Brand

## Istruzioni

Quando l'utente invoca `/create-brand [nome-brand]`, avvia il processo di onboarding per un nuovo brand seguendo questo workflow:

### Step 1 — Verifica Prerequisiti
1. Controlla che `brands/[nome-brand]/` non esista gia'. Se esiste, avvisa l'utente e chiedi se vuole sovrascrivere.
2. Leggi `framework/content-frameworks.md` per avere i template disponibili (L1-L8, V1-V6, S1-S3).
3. Leggi un brand esistente (es. `brands/ai-social-media-manager/brand-voice.md`) come riferimento per il formato e la qualita' attesa.

### Step 1b — Determina la Modalita' di Input
Il brand puo' essere creato in 3 modi:

**Modalita' A — Da documenti/sorgenti (automatica)**
Se l'utente fornisce materiale sorgente (repo con codice, slide, PDF, documenti di presentazione, sito web), estrai automaticamente tutte le informazioni possibili:
- Leggi i file forniti (codice, README, slide, docs) con `Read`
- Se e' un sito web, usa `WebFetch` per estrarre info
- Ricava: nome, cosa fa, differenziatore, settore, tono, target audience
- Procedi direttamente allo Step 3b per conferma, saltando le interviste
- Chiedi all'utente SOLO cio' che non riesci a dedurre dai materiali

**Modalita' B — Intervista guidata (interattiva)**
Se l'utente non fornisce materiale, avvia l'intervista (Step 2-4).

**Modalita' C — Ibrida**
L'utente fornisce materiale parziale + risponde a domande specifiche per le info mancanti.

Chiedi all'utente quale modalita' preferisce, oppure deducilo dal contesto (es. se dice "crea un brand dal mio repo", usa Modalita' A).

### Step 2 — Intervista: Identita' del Brand
*(Solo se Modalita' B o C — salta se le info sono gia' state estratte dai documenti)*

Chiedi all'utente (con `AskUserQuestion` dove possibile):

- **Nome brand** e tagline (se ne ha una)
- **Cosa fa** il prodotto/servizio (descrizione breve, 1-2 frasi)
- **Differenziatore** chiave rispetto ai competitor (la "unique selling proposition")
- **Settore** e mercato target (B2B/B2C, area geografica, dimensione aziende target)
- **Fondatori/speaker** (chi saranno le facce del brand nei contenuti — nome, ruolo, tono)

### Step 3 — Intervista: Audience e Tono
*(Solo se Modalita' B o C — salta se le info sono gia' state estratte dai documenti)*

Chiedi all'utente:

- **Personas** (2-4): per ciascuna, chiedi ruolo, eta', frustrazioni principali, obiettivi, linguaggio usato
- **Tono** desiderato: proponi una scala su 3 assi:
  - Formale ↔ Informale
  - Serio ↔ Ironico
  - Tecnico ↔ Accessibile
- Se l'utente non sa, proponi combinazioni basate sul settore (es. "Per un SaaS B2B, consiglierei: informale + leggermente ironico + accessibile")
- **Piattaforme** prioritarie (LinkedIn, Instagram, TikTok, YouTube — ordina per priorita')

### Step 3b — Conferma Info Estratte (solo Modalita' A)
Se hai estratto le info dai documenti, presenta un riepilogo:
- Cosa ho capito del brand (nome, prodotto, differenziatore, settore)
- Personas che propongo (basate sul target dedotto)
- Tono che propongo (basato sul materiale analizzato)
- Chiedi conferma: "E' corretto? Vuoi cambiare qualcosa?"

### Step 4 — Ricerca Competitor (automatica)
**NON chiedere i competitor all'utente.** Cercali autonomamente:

1. Usa `WebSearch` per cercare competitor nel settore del brand:
   - "[settore] competitor [mercato target]"
   - "[tipo prodotto] alternative"
   - "migliori [categoria] Italia" (se mercato italiano)
2. Identifica 3-6 competitor rilevanti
3. Per ogni competitor, raccogli con `WebSearch` e `WebFetch`:
   - Cosa fanno, posizionamento, pricing
   - Come comunicano sui social (tono, frequenza, piattaforme)
   - Punti di forza e debolezza nel content marketing
4. Se l'utente menziona competitor specifici, includili e aggiungine altri dalla ricerca
5. Presenta i competitor trovati all'utente per conferma

### Step 4b — Strategia Contenuti
Definisci (proponendo default sensati basati su settore e competitor):

- **Content pillar** (3-5): temi principali attorno a cui ruotano i contenuti. Proponi basandoti su settore, competitor e posizionamento
- **Funnel**: come distribuire i contenuti tra TOFU (awareness) / MOFU (consideration) / BOFU (conversion). Proponi la distribuzione S1 (30/40/20/10) come default
- **Livello brand** nei contenuti: quanto il brand deve essere presente
  - 0 = mai nominato (65% dei contenuti)
  - 1 = implicito
  - 2 = accenno
  - 3 = case study
  - 4 = vendita diretta (max 10% dei contenuti)
- **Riferimenti**: brand che ammirano per il tono, creator che seguono, contenuti che vorrebbero emulare

### Step 5 — Genera i File del Brand
Con tutte le info raccolte, crea `brands/[nome-brand]/` con questa struttura:

| File | Contenuto |
|------|-----------|
| `brand-voice.md` | Identita', voce, StoryBrand applicato (eroe = cliente, guida = brand), regole d'oro, do/don't |
| `content-pillars.md` | I 3-5 pillar con: descrizione, tono, personas target, frequenza, funnel position, framework consigliati |
| `audience-personas.md` | Profili dettagliati delle 2-4 personas: nome fittizio, ruolo, eta', frustrazioni, obiettivi, linguaggio, come trovano contenuti, cosa li convince |
| `tono-infotainment.md` | Guida al tono specifico del brand: pattern linguistici, parole da usare, parole da evitare, esempi di frasi nel tono giusto vs sbagliato |
| `expert-applications.md` | File con header e template vuoto — pronto per future applicazioni degli esperti al brand |
| `framework-examples.md` | 2-3 esempi compilati dei framework L/V usando il nuovo brand (un L1 o L4 + un V1 o V6 come minimo) |
| `competitors/README.md` | Lista competitor con breve descrizione e posizionamento rispetto al brand |
| `content-library/linkedin/.gitkeep` | Directory pronta per i contenuti LinkedIn |
| `content-library/video/instagram/.gitkeep` | Directory pronta per Reels |
| `content-library/video/tiktok/.gitkeep` | Directory pronta per TikTok |
| `content-library/video/youtube/.gitkeep` | Directory pronta per YouTube |

**Formato dei file**: usa lo stesso stile e struttura dei file in `brands/mastrohr/` come riferimento.

### Step 6 — Presenta e Valida
1. Mostra un riepilogo di tutto cio' che e' stato creato:
   - Numero di file generati
   - Personas definite
   - Pillar scelti
   - Piattaforme configurate
2. Mostra un'anteprima del `brand-voice.md` generato
3. Chiedi conferma all'utente: "Tutto corretto? Vuoi modificare qualcosa?"
4. Se l'utente conferma, suggerisci i prossimi passi:
   - "Vuoi generare un primo contenuto? Usa `/linkedin-post [topic]`"
   - "Vuoi generare uno script video? Usa `/video-script [topic]`"
   - "Vuoi cercare idee per contenuti? Usa `/content-ideas [tema]`"

## Note Importanti

- **Lingua**: tutto in italiano. Termini tecnici inglesi dove naturale nel settore del brand.
- **Qualita'**: i file generati devono essere completi e operativi, non placeholder. Il brand deve poter iniziare a generare contenuti subito dopo il setup.
- **StoryBrand**: applica sempre il framework di Donald Miller — l'eroe e' il cliente, il brand e' la guida.
- **Competitor**: cerca SEMPRE i competitor automaticamente con `WebSearch`. Non chiedere all'utente di elencarli — trovalo tu e chiedi conferma.
- **Input da documenti**: quando l'utente fornisce materiale sorgente (repo, slide, PDF, sito), estrai il massimo possibile e chiedi solo le info mancanti. L'obiettivo e' minimizzare le domande.
- **Flessibilita'**: non tutte le domande sono obbligatorie. Se l'utente non sa rispondere a qualcosa, proponi default sensati basati sul settore.

## Esempi di Invocazione

- `/create-brand "acme-saas"` — avvia l'onboarding interattivo per il brand "acme-saas"
- `/create-brand "acme-saas"` + "ecco il repo: github.com/acme/saas" — estrae info dal repo e crea il brand automaticamente
- `/create-brand "acme-saas"` + "ti allego le slide di presentazione" — estrae info dalle slide
- `/create-brand "green-energy"` + "ecco il nostro sito: green-energy.com" — analizza il sito e crea il brand
- `/create-brand "studio-legale-rossi"` — configura un brand per uno studio legale (intervista guidata)
