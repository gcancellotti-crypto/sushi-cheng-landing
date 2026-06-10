# Sushi Cheng Perugia — Landing Page
## Recap di Progetto

---

## 📍 Info Cliente

| | |
|---|---|
| **Cliente** | Sushi Cheng Perugia |
| **Indirizzo** | Via Giuseppe Minottini, 6 — 06128 Perugia PG |
| **Telefono** | 075 697 1681 / WhatsApp ordini: +39 380 646 3740 |
| **Rating Google** | 4.6 ★ · 1.716 recensioni |
| **Fascia prezzi** | 20–30 € |

---

## 🌐 URL & Deploy

| | |
|---|---|
| **URL live** | `frolicking-moonbeam-8994bb.netlify.app` |
| **Piattaforma** | Netlify |
| **Comando deploy** | `netlify deploy --prod` |
| **Cartella progetto** | `~/Documents/DEV/sushi-cheng-landing` |

---

## 💰 Pricing Concordato

| Voce | Importo |
|---|---|
| **Una tantum** (sviluppo landing) | €700,00 |
| **Canone mensile** (gestione) | €100,00/mese |

---

## 🛠 Stack Tecnico

- **HTML / CSS / JavaScript** vanilla — nessun framework
- **Font:** Ivyora Display (Adobe Typekit) + Alkaline + Helvetica Neue
- **Palette:** Dark mode `#0a0a0a` / Light mode `#f5f3ef` — bianco/nero/grigio
- **Deploy:** Netlify (drag & drop o CLI)
- **WhatsApp API:** `wa.me` con messaggio pre-compilato
- **Logo:** CDN Netlify (`logo cheng white png.png`) con inversione automatica in light mode

---

## ✅ Funzionalità Implementate

### Home
- Logo + tagline
- 2 CTA button: **Prenota un tavolo** / **Ordina asporto**
- Offerta asporto in evidenza (testo tipografico, no riquadro)
- Gallery fotografica drag-to-scroll
- Mappa Google embedded (grayscale in dark mode)
- Sezione recensioni con score 4.6★ e review card scrollabili
- Review sheet (bottom sheet con recensione completa al tap)
- Dark / Light mode toggle con localStorage
- Animazioni fade-in on scroll

### Vista Prenotazione
- Form: nome, cognome, telefono, data, orario, coperti, note
- Validazione campi obbligatori
- Submit → apertura WhatsApp con messaggio precompilato

### Vista Asporto
- Menù completo con categorie e pulsanti +/−
- **Dish sheet** al tap su ogni piatto: nome, descrizione, prezzo, +/− carrello
- Carrello sticky in basso con badge contatore
- Logica promo: **8 piatti = €28,90** (menù fisso)
- Cart sheet con riepilogo ordine, totale e nota promo
- Form ritiro: nome, telefono, orario
- Submit → apertura WhatsApp con ordine dettagliato

### Tecnico
- Router client-side con History API (3 viste: home / prenota / asporto)
- Animazione `pageIn` sulle transizioni di vista
- Drag-to-scroll su gallery e recensioni (desktop)
- Toast di errore per campi mancanti
- Safe area inset per iPhone notch

---

## 🍱 Menù Implementato

Categorie presenti in `index.html` (aggiornato da Glovo/JustEat + menu1.pdf):

1. Antipasti
2. Antipasti Classici
3. Sashimi (3 pz)
4. Nigiri (2 pz)
5. Uramaki Classici (4 pz)
6. Black Roll (4 pz)
7. Special Roll (4 pz)
8. Hossomaki (6 pz)
9. Futomaki (4 pz)
10. Poke Bowls
11. Secondi Piatti
12. Fritti

> ⚠️ I prezzi sono stati aggiornati da `menu1.pdf`. Verificare con il cliente eventuali variazioni stagionali.

---

## 📋 Prossimi Step

- [ ] Verificare prezzi finali con il cliente dopo integrazione `menu1.pdf`
- [ ] Ottenere foto ufficiali dei piatti dal ristorante (per eventuale upgrade futuro)
- [ ] Dominio custom (es. `sushichengperugia.it`) da collegare a Netlify
- [ ] Condividere URL live al cliente per approvazione
- [ ] Fattura una tantum €700 + attivazione canone €100/mese

---

## 🖥 Comandi Utili

```bash
# Aprire il progetto con Claude Code
cd ~/Documents/DEV/sushi-cheng-landing && claude --dangerously-skip-permissions

# Deploy su Netlify
cd ~/Documents/DEV/sushi-cheng-landing
netlify deploy --prod

# Anteprima locale (se hai un server locale)
npx serve .
```

---

## 📁 Struttura File

```
sushi-cheng-landing/
├── index.html          # File principale (tutto in uno)
├── menu1.pdf           # Menù ufficiale del ristorante
└── img/
    └── (eventuali foto future)
```

---

*Progetto gestito da: [il tuo nome/studio]*
*Ultimo aggiornamento: Giugno 2026*
