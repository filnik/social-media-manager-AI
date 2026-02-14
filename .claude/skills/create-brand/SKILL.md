---
name: create-brand
description: Crea la configurazione completa per un nuovo brand. Intervista l'utente per raccogliere informazioni e genera tutti i file necessari in brands/[nome-brand]/.
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
3. Leggi un brand esistente (es. `brands/mastrohr/brand-voice.md`) come riferimento per il formato e la qualita' attesa.

### Step 2 — Intervista: Identita' del Brand
Chiedi all'utente (con `AskUserQuestion` dove possibile):

- **Nome brand** e tagline (se ne ha una)
- **Cosa fa** il prodotto/servizio (descrizione breve, 1-2 frasi)
- **Differenziatore** chiave rispetto ai competitor (la "unique selling proposition")
- **Settore** e mercato target (B2B/B2C, area geografica, dimensione aziende target)
- **Fondatori/speaker** (chi saranno le facce del brand nei contenuti — nome, ruolo, tono)
- **Competitor** principali (3-5 nomi)

### Step 3 — Intervista: Audience e Tono
Chiedi all'utente:

- **Personas** (2-4): per ciascuna, chiedi ruolo, eta', frustrazioni principali, obiettivi, linguaggio usato
- **Tono** desiderato: proponi una scala su 3 assi:
  - Formale ↔ Informale
  - Serio ↔ Ironico
  - Tecnico ↔ Accessibile
- Se l'utente non sa, proponi combinazioni basate sul settore (es. "Per un SaaS B2B, consiglierei: informale + leggermente ironico + accessibile")
- **Piattaforme** prioritarie (LinkedIn, Instagram, TikTok, YouTube — ordina per priorita')

### Step 4 — Intervista: Strategia Contenuti
Chiedi all'utente:

- **Content pillar** (3-5): temi principali attorno a cui ruotano i contenuti. Se l'utente non sa, proponi basandoti su settore e competitor
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
- **Ricerca**: se l'utente fornisce i competitor, usa `WebSearch` per raccogliere info su posizionamento e tono dei competitor.
- **Flessibilita'**: non tutte le domande sono obbligatorie. Se l'utente non sa rispondere a qualcosa, proponi default sensati basati sul settore.

## Esempi di Invocazione

- `/create-brand "acme-saas"` — avvia l'onboarding per il brand "acme-saas"
- `/create-brand "green-energy"` — crea setup per un brand nel settore energia verde
- `/create-brand "studio-legale-rossi"` — configura un brand per uno studio legale
