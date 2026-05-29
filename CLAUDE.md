# Sushi Cheng Landing Page

Landing page mobile-first per il ristorante **Sushi Cheng** di Perugia.
Raggiunta tramite link in Stories Instagram — ottimizzata esclusivamente per smartphone.

## Stack

- Singolo file `index.html` — HTML + CSS + JS vanilla
- Zero dipendenze esterne, zero build step
- Nessun backend: i form aprono WhatsApp via `wa.me`

## Struttura file

```
sushi-cheng-landing/
├── index.html          ← tutta la pagina
├── CLAUDE.md
└── assets/
    ├── images/         ← (vuota, pronta per logo/foto)
    └── fonts/          ← (vuota, pronta per font custom)
```

## Design

| Token | Dark | Light |
|-------|------|-------|
| `--bg` | `#0a0a0a` | `#f5f3ef` |
| `--text` | `#ffffff` | `#1a1a1a` |
| `--accent` | `#ffffff` (bianco) | `#1a1a1a` (nero) |
| `--on-accent` | `#0a0a0a` | `#ffffff` |
| `--border` | `#2a2a2a` | `#d8d4cc` |
| Font titoli | `ivyora-display` (serif) — via Adobe Typekit kit `tzn8ozv` ||
| Font sottotitoli | `alkaline` (sans-serif) — via Adobe Typekit kit `tzn8ozv` ||
| Font body | `Helvetica Neue` weight 300 (Light) ||

**Palette monocromatica** — nessun colore rosso. L'accent è bianco in dark, nero in light. `--on-accent` garantisce leggibilità del testo su sfondi accentuati (cart bar, bottoni primari).

- Supporto dark/light mode tramite classe `.light` su `<html>`; preferenza salvata in `localStorage` con chiave `sc-theme`
- Pulsante toggle fisso top-right (☀/🌙), z-index 300
- Layout 100% width, nessun max-width — occupa tutta la viewport mobile
- Padding laterale fisso: **16px** ovunque
- Bottoni `min-height: 56–60px` per uso touch
- Animazioni fade-in su scroll via `IntersectionObserver`

## Router (hash-based SPA)

Tre viste gestite da `history.pushState` + `popstate`. Navigazione tramite `data-goto="..."`.

| Vista | ID DOM | URL |
|-------|--------|-----|
| Home | `view-home` | `/` |
| Prenota | `view-prenota` | `#prenota` |
| Asporto | `view-asporto` | `#asporto` |

Il tasto back del telefono funziona correttamente via `popstate`. Animazione `pageIn` (slide da destra) sulle view non-home.

## Sezioni

### 1 — Home (`view-home`)
Full-viewport (`min-height: 100svh`), logo (320px) + 2 bottoni + gallery orizzontale a scorrimento.
Gallery: 5 immagini in `assets/images/gallery/`, scroll-snap orizzontale, drag-to-scroll desktop. Immagini `72vw` (max 280px), `aspect-ratio: 4/3`, `border-radius: 14px`. Footer in fondo.
Mappa Google Maps iframe (`filter: grayscale(1)` in dark, colori in light), indirizzo: **Via Giuseppe Minottini, 6, 06128 Perugia PG**, link "Apri Maps →".
Recensioni: strip orizzontale scroll-snap sotto la mappa, label "Cosa dicono i clienti". Card HTML trascritte dalle immagini: 1 summary card (4.6★ · 1.7K Google) + 5 card individuali (Marco Ago, Linda Ferranti, Nicola Ciampica, Enrico C., Nicole G.), tutte 5/5. Testo troncato a 6 righe via `-webkit-line-clamp`.

### 2 — Prenota un Tavolo (`view-prenota`)
Vista separata con nav bar sticky (`← Indietro`). Animazione slide-in da destra.
Form: Nome, Cognome, Telefono, Data, Orario (10 slot), Coperti (1–10), Note.
Submit → costruisce messaggio e apre:
```
https://wa.me/393806463740?text=[messaggio_url_encoded]
```

Formato messaggio:
```
🍽 PRENOTAZIONE TAVOLO — Sushi Cheng
👤 Nome: [nome] [cognome]
📞 Telefono: [telefono]
📅 Data: [gg/mm/aaaa]
🕐 Orario: [orario]
👥 Coperti: [n]
📝 Note: [note o "nessuna"]
```

### 3 — Ordina Asporto (`#asporto`) — sezione panel
Nascosta di default. Si apre via `openPanel('asporto')`. Stesso comportamento della sezione prenota.
Menù interattivo con 12 categorie e ~60 piatti, pulsanti +/− per ogni voce.
Carrello sticky in basso (cart bar rossa) → bottom sheet con riepilogo + form checkout.

Form checkout: toggle **Ritiro / Consegna**, Nome, Telefono, Indirizzo (solo se Consegna), Orario (9 slot, label dinamica).
Submit → apre WhatsApp con ordine completo:
```
🥡 ORDINE ASPORTO — Sushi Cheng
👤 Nome: [nome]
📞 Telefono: [telefono]
🕐 Ritiro: [orario]
📋 Ordine:
• [piatto] x[n] — €[subtotale]
💰 Totale: €[totale]
```

## Numero WhatsApp

`+39 380 646 3740` → `393806463740`

## Categorie menù

Antipasti · Antipasti Classici · Secondi Piatti · Nigiri (2 pz) · Special Roll (4 pz) ·
Uramaki Classici (4 pz) · Black Roll (4 pz) · Futomaki · Hossomaki (6 pz) ·
Poke Bowls · Sashimi (3 pz) · Fritti

## Note di sviluppo

- Tema: dark default (`#0a0a0a`), light (`#f5f3ef`); toggle via `:root.light`, JS in IIFE all'avvio, persist `localStorage` chiave `sc-theme`
- Font caricati via `@import` Adobe Typekit (kit `tzn8ozv`) in cima al CSS — richiedono connessione internet; fallback: Georgia (serif), Helvetica Neue (sans)
- CSS variables font: `--font-title` → ivyora-display, `--font-sub` → alkaline, `--font` → Helvetica Neue 300
- La data nel form prenotazione ha `min` impostato a oggi via JS
- Il carrello si aggiorna sia nel menu principale che nel bottom sheet (stato condiviso in `cart` object)
- Il cart bar usa `left: 0; right: 0` (no `translateX`) per evitare problemi su viewport mobile
- Il toast usa `left: 16px; right: 16px` invece di centrarsi con `left: 50%`
- `safe-area-inset-bottom` applicato a cart bar e cart sheet per iPhone con notch

## Changelog

| Data | Modifica |
|------|----------|
| 2026-05-29 | Creazione pagina completa (Hero + form prenotazione + menù asporto con carrello) |
| 2026-05-29 | Ottimizzazione mobile-only: rimosso max-width 430px, rimossa centratura desktop, padding 16px, font size aumentati, cart bar/sheet full-width |
| 2026-05-29 | Creata struttura `assets/images/` e `assets/fonts/` |
| 2026-05-29 | Implementati font Adobe Typekit: ivyora-display (titoli), alkaline (sottotitoli), Helvetica Neue 300 (body) |
| 2026-05-29 | Dark/light mode toggle: pulsante fisso top-right, classe `.light` su `<html>`, persist localStorage |
| 2026-05-29 | Logo immagine nell'hero (sostituisce testo); `filter: invert(1)` in light mode |
| 2026-05-29 | Palette monocromatica: rimosso rosso, accent = bianco/nero, variabile `--on-accent`; logo 320px |
| 2026-05-29 | Hero full-viewport con solo logo+bottoni; sezioni diventano pannelli nascosti aperti via JS (`openPanel`/`closePanel`) |
