# Designsystem: Profil Rejser

Dokumenteret på baggrund af analyse af [profil-rejser.dk](https://www.profil-rejser.dk/) — april 2026.

---

## Farvepalet

| Rolle | Farve | Hex |
|-------|-------|-----|
| Primær (navy) | ████ | `#1A2C41` |
| Hvid | ████ | `#FFFFFF` |
| Lys baggrund | ████ | `#F3F1ED` |
| Tekst (sort) | ████ | `#000000` |
| Tekst (mørkegrå) | ████ | `#545454` |
| Tekst (sekundær) | ████ | `#313131` |
| Accent (guld/bronze) | ████ | `#9F8974` |
| Accent (lyseblå) | ████ | `#67AEFF` |

**Overlays:**
- Billedoverlays bruger `rgba(0,0,0,0.30–0.50)` eller primærfarven `#1A2C41` med opacity
- Kort bruger enten guld `#9F8974` eller navy `#1A2C41` som overlay

---

## Typografi

**Skrifttyper:**
- Overskrifter: **Zahrah** (serif, loaded lokalt som woff2) — vægt: Light (300)
- Brødtekst og UI: **DM Sans** (sans-serif, loaded lokalt som woff2) — vægte: Regular + Bold

**Størrelser (WordPress presets):**
- Small: `13px`
- Medium: `20px`
- Large: `36px`
- X-Large: `42px`
- Brødtekst: `16px` (standard)

**Vægte:**
- Regular/normal — sitet bruger generelt lette vægte, ingen fed tekst dominerer

---

## Spacing og layout

**Container:**
- Styres via `--wp-style--global--content-size` og `--wp-style--global--wide-size`
- WordPress block-baseret layout med `is-layout-flex` og `is-layout-flow`

**Spacing-presets:**
- M: `1rem` (16px)
- L: `1.25rem` (20px)
- XL: `1.5rem` (24px)
- Grid gap: `0.5em`

**Breakpoints:**
- Mobil: `max-width: 600px`
- Responsivt: Sitet stacker kolonner på mobil, typisk 1 kolonne

---

## Komponenter

### Header / Navigation
- **Logo:** Profil Rejser SVG-logo, blå variant — skifter til sort ved scroll
- **Primær navigation:** "Find destination", "Find krydstogt (Bella Vista)", "Firmarejser"
- **Sekundær navigation:** Destinationsgrupper, Oplevelser, Rejseinspiration, Find rejseekspert
- **Søg:** Raffle.ai-integration
- **CTA i header:** "Få et tilbud" — primær knap

### Hero / Banner
- Fuldbredde billede (op til 2560×1600px) med mørkt overlay (opacity ~0.30)
- Overlay-farve: `#1A2C41`
- Stor hvid overskrift centreret
- Undertekst/beskrivelse under overskriften
- Bruges på alle overordnede sider (forside, destinationer, inspiration)

### Knapper
- **Primær:** Baggrund `#1A2C41`, hvid tekst, `border-radius: 9999px` (pill-shape)
- **Padding:** `calc(.667em + 2px) calc(1.333em + 2px)`
- **Hover:** Transparent baggrund, blå tekst, border synlig
- **Sekundær:** Outline-variant med border og transparent baggrund

### Destinationskort (Card)
- Billedbaggrund med farveoverlay (20–30% opacity)
- Portrætformat: ca. 340×500px
- Titel som hvid tekst over billedet
- Hele kortet er klikbart
- Bruges til: destinationer, oplevelseskategorier

### Rejsekort (Rejseforslag)
- Billedbaggrund med overlay
- Titel + prisangivelse synlig
- Bruges i grid (typisk 3 kolonner desktop, 1 kolonne mobil)

### Artikelkort (Inspiration)
- Billedbaggrund med let overlay
- Titel som overlay-tekst
- Ingen synlige metadata (dato, kategori, forfatter)
- Klasse: `card-automatic` med dynamisk baggrundsfarve

### Graphic Bow (Billede + tekst)
- Sektion med billede på den ene side, tekst + CTA på den anden
- Bruges til feature-sektioner, ekspertcitater
- Veksler mellem billede-venstre og billede-højre

### Rejseekspert-profil
- Profilbillede (landskabsformat, ca. 1000×615px)
- Navn, titel, kontaktinfo
- Direkte kontakt-CTA (telefon, e-mail)
- Personlig og tillidsopbyggende

### Vejr-widget
- Temperatur og nedbørsdata for destinationen
- Tabellayout med månedsvisning

### Nyhedsbrev / Formular
- HubSpot-integreret tilmeldingsformular
- Overskrift + kort beskrivelse + inputfelt + knap
- Bruges i bunden af de fleste sider

### Footer
- 5-kolonne layout
- Kolonner: Rejseinspiration, Kontakt, Om os, Praktisk, Sociale medier
- Sociale ikoner: Facebook, Instagram, LinkedIn
- Kontaktinfo: Telefon, CVR-nummer, Rejsegarantifonden

---

## Sidetyper

### 1. Forside
Hero (video/billede) → Featured destinationer (3-kolonne grid) → Graphic bow-sektioner → Inspirationskort → CTA/nyhedsbrev → Footer

### 2. Destinationsside (f.eks. Thailand)
Hero → Introduktionstekst → Destinationskort (underkategorier) → Populære rejsemål (linkliste) → Rejseforslag (priskort) → Inspirationsartikler → Rejseekspert-profil → Oplevelseskategorier → Vejr-widget → Nyhedsbrev → Footer

### 3. Inspirationsside
Hero → Breadcrumbs → Introduktion → Featured stories (store kort) → Artikelgrid → Rejseekspert-finder → Events → Magasin → Nyhedsbrev → Footer

---

## Billedstil

- **CDN:** Cloudflare med `fit=cover, format=auto, quality=80`
- **Gravity:** Auto eller specifik (`0.52x0.3`) for smart cropping
- **Motiver:** Autentiske rejsefotos — natur, mennesker, kultur, mad
- **Behandling:** Naturlige farver, ingen filtre — overlays tilføjes i CSS
- **Formater:** Portrætformat (340×500) til kort, landskab (1000×615) til profiler og features

---

## Tone og sprog

- **Inspirerende og poetisk:** "Thailand er et land af muligheder. Kontraster. Men altid i farver."
- **Personlig:** Navngivne eksperter med direkte kontaktinfo
- **Informativ men ikke teknisk:** Guide-agtig, oplevelsesfokuseret
- **Eventyr-orienteret:** "drømmer", "autentiske", "oplev"
- **Naturligt dansk:** Ingen overdrevent salgssprog
- **CTA-stil:** Blød men tydelig — "Få et tilbud", "Ring til os", "Se rejser"
