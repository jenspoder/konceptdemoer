# Designsystem — Experimentarium

> Dokumenteret april 2026 på baggrund af [experimentarium.dk](https://experimentarium.dk/)
> Experimentarium er "hele Danmarks science center" — et interaktivt, familievenligt videnskabsmuseum i Hellerup.

---

## 1. Visuel identitet

### Farvepalet

Experimentarium bruger et **tema-baseret farvesystem** med fire temafarver, der skifter afhængigt af sektion/side:

| Rolle | Navn | Hex | Anvendelse |
|-------|------|-----|------------|
| **Primær / Theme Blue** | Blå | `#0095ff` | Standard temafarve, knapper, links, navigation |
| **Theme Green** | Grøn | `#00e14b` | Alternativt tema |
| **Theme Red** | Rød/koral | `#f83d4e` | Alternativt tema |
| **Theme Lavanda** | Lavendel | `#d885ff` | Alternativt tema |
| **Baggrund (mørk)** | Mørkeblå/navy | `#0b1326` | Footer, mørke sektioner, body-tekst |
| **Baggrund (lys)** | Næsten hvid | `#fefefe` | Body baggrund |
| **Tekst** | Næsten sort | `#0a0a0a` | Brødtekst |
| **Tekst (lys)** | Hvid | `#ffffff` | Tekst på mørke baggrunde |
| **Accent / sekundær** | Gul | `#f7c537` | Sporadisk accent |
| **Grå (meta)** | Mellemgrå | `#787c85` / `#6b7792` | Meta-tekst, sekundær info |

Hver temafarve har også en transparent variant (26% opacity) til baggrunde:
- Blå: `#0095ff26`
- Grøn: `#00e14b26`
- Rød: `#f83d4e26`
- Lavendel: `#d885ff26`

### Typografi

**Skriftfamilier:**

| Font | Type | Anvendelse |
|------|------|------------|
| **EXP-display** | Display / custom | Overskrifter (uppercase), sektions-headers |
| **Mark Pro** | Sans-serif / custom | Sekundære overskrifter, fed tekst, labels |
| **Helvetica Neue, Helvetica, Roboto, Arial** | System sans-serif | Brødtekst (body fallback) |

**Skriftstørrelser:**

| Element | Størrelse (mobil) | Størrelse (desktop, ≥40em) | Vægt | Linjehøjde |
|---------|-------------------|----------------------------|------|------------|
| `.header--large` | `2em` | `4em` | 400 | 1.25 |
| `.header--medium` | `1.5em` | `2.5em` | 400 | 1.0 (desktop) |
| `.header--small` | `1.25em` | `1.5em` | 800 | 1.25 |
| `.header--smaller` | `1.2em` | `1.2em` | 800 | 1.35 |
| `.header--nano` | `1em` | `1em` | 800 | 1.25 |
| Body | `100%` (16px) | `100%` (16px) | 400 | 1.5 |
| `.text--small` / meta | `12px` | `12px` | 400 | 1.25em |

**Overskrifter bruger EXP-display** med `text-transform: uppercase` og `font-weight: 400` (displayfonten er allerede visuelt tung).

**Mark Pro** har vægtene: 100 (thin), 500 (medium), 700 (bold), 800 (extra bold), 900 (black) — samt tilhørende italic-varianter.

---

## 2. Komponenter

### Navigation (header)

**Struktur:**
- Fast positioneret (`position: fixed`) top-navigation med `z-index: 100`
- Tre kolonner på mobil (logo venstre, hamburger center, CTA højre)
- Desktop: Logo + mega-menu + sekundær nav + "Køb billet" CTA

**Elementer:**
- `.global-navigation` — wrapper, fuld bredde
- `.global-navigation__nav-items` — primær menu (mega-menu via MaxMegaMenu plugin)
- `.global-navigation__secondary-nav` — sekundær navigation (font-size: 12px)
- `.global-navigation__webshop` — webshop-link (font-size: 12px)
- Off-canvas menu (`.off-canvas-menu`) til mobil

**Mega-menu:**
- Baggrund: `#222` (desktop)
- Links: `#666` default, `#ffffff` active/hover
- Hover/active baggrund: `#333`
- Breakpoint: 600px (mobil/desktop skift)
- Fade-up animation på sub-menus (200ms ease-in)

**Primære menupunkter:** Besøg, Oplevelser, Videnskab, Skole & dagtilbud, Erhverv, Entré

### Knapper (`.btn`)

**Primær knap:**
```css
display: inline-block;
font-size: 17px;
font-weight: 800;
background-color: transparent;
color: #0095ff;              /* temafarve */
border: 0.175em solid #0095ff;
padding: 15px 40px;
cursor: pointer;
transition: all 0.3s cubic-bezier(0, 0.85, 0.49, 1);
```

**Hover-state:**
```css
background-color: #0095ff;  /* fylder op med temafarve */
color: #fff;
```

**Hover-animation:** Teksten glider op og forsvinder, en kopi (`data-text` attribut) glider ind nedefra — elegant "swap"-effekt via `transform: translate3d()`.

**Varianter:**
- `.btn--large` — `font-size: 25.5px`
- `.btn--small` — mindre variant
- `.btn--black` — sort variant
- `.btn--invert` — inverteret farve
- `.label-btn` — label-stil knap, deler basis-styling med `.btn`

**Tema-varianter:** Knapfarven ændres automatisk via `.theme-blue`, `.theme-green`, `.theme-red`, `.theme-lavanda` klasserne på parent-elementet.

### Kort / Cards

**Thumbnail-default (standard card):**
```
┌──────────────────────┐
│      Billede          │  .thumbnail__image
│   (ca. 387×217px)     │
├──────────────────────┤
│  Titel (h3)           │  .thumbnail__content
│  Meta (dato, sted)    │  .text--small.meta
│  Tags                 │  .tags
└──────────────────────┘
```

- `.thumbnail__content` — `margin: 20px 20px 0`
- Titel: `font-size: 1.2em`, `font-weight: 800`, `line-height: 1.35`
- Meta: `font-size: 12px`
- Tags: `margin: 1em 0`

**Card-varianter:**
- `.thumbnail-default--event` — eventcard med dato/sted
- `.thumbnail-default--product` — produktcard med label-btn
- `.thumbnail-blanc` — hvidt card med skygge (`box-shadow: 0 5px 20px #00000040`)
- `.thumbnail-focus` — featured/fokus card med stor titel (`font-size: 2.5em`, EXP-display)
- `.thumbnail-top5` — top-5 listekort
- `.thumbnails-exhibition` — udstillingskort

### Hero / Banner

**Hero-top:**
```css
position: relative;
overflow: hidden;
height: calc(80vh - 70px);    /* mobil */
height: calc(85vh - 100px);   /* tablet */
height: calc(90vh - 100px);   /* desktop */
```

- Fuldbreds billede/video som baggrund
- Indhold med `.hero__content` — tekst overlay
- `.hero__content .info p` — `font-size: 1.25em` → `1.4em` (desktop)
- Video-afspilningsknap: hvid border, padding `12px 40px 12px 20px`, font-size `13px`

**Hero-grid (forside):**
- Grid af `.hero-grid--item` elementer (8 stk. på forsiden)
- Hvert item har: `.hero-grid--background` (billede), `.hero-grid--title` (tekst), `.hero-grid--link`
- Bruges til at vise udstillinger/oplevelser visuelt

### Meta-info / ikoner

Detailsider viser meta-information med ikoner:
- Aldersgruppe (f.eks. "Fra 8 år") — `age.svg`
- Varighed (f.eks. "20-30 minutter") — `time.svg`
- Kategori/fag — `tag.svg`
- Vist horisontalt under overskriften

### Footer

```css
background-color: #0b1326;
color: #fff;
padding: 40px 0;
```

**Indhold:**
- Åbningstider (`.opening-time` liste med `.day` inline-block, min-width: 50px)
- Adresse: Tuborg Havnevej 7, 2900 Hellerup
- Kontakt: telefon + email
- CVR-nummer
- Nyhedsbrev-signup
- Sociale medier: Facebook, Instagram, LinkedIn, TikTok, YouTube
- Juridisk: Cookies, privatlivspolitik
- Partner-logoer (Top Attraktioner, VPAC)

**Footer links:** `border-bottom: 1px solid white`, forsvinder ved hover.
**Footer overskrifter (h5):** `font-weight: 800`

---

## 3. Layout og spacing

### Grid-system

Baseret på **Foundation** framework:
- 12-kolonne grid
- Breakpoints: `small: 0em`, `medium: 40em` (640px), `large: 64em` (1024px), `xlarge: 75em` (1200px), `xxlarge: 90em` (1440px)
- `.row` / `.columns` system
- Flexbox-baseret alignment (`.align-center`, etc.)

### Spacing

WP spacing-scale (CSS custom properties):
```css
--wp--preset--spacing--20: 0.44rem;
--wp--preset--spacing--30: 0.67rem;
--wp--preset--spacing--40: 1rem;
--wp--preset--spacing--50: 1.5rem;
--wp--preset--spacing--60: 2.25rem;
--wp--preset--spacing--70: 3.38rem;
--wp--preset--spacing--80: 5.06rem;
```

Generelt:
- Card margin-bottom: `40px` (`.thumbnail-blanc`)
- Footer item margin-bottom: `20px`
- Section padding varierer, men typisk `40px` vertikalt

### Shadows

```css
--wp--preset--shadow--natural: 6px 6px 9px rgba(0, 0, 0, 0.2);
--wp--preset--shadow--deep: 12px 12px 50px rgba(0, 0, 0, 0.4);
```

Card shadows:
- `.thumbnail-blanc .thumbnail__image` — `box-shadow: 0 5px 20px #00000040`
- `.thumbnail-blanc .thumbnail__content` — `box-shadow: 0 10px 40px -5px #0000001a`

---

## 4. Sidetyper

### Forside
- Hero-grid med 8 visuelle blokke (udstillinger/oplevelser)
- "Det sker i dag" — dagsprogram med tidspunkter og lokationer
- Udstillings-thumbnails i grid (`.thumbnails-exhibition`)
- Events-sektion med `.thumbnail-default--event` cards
- Nyhedsbrev-signup
- Footer

### Listeside (Udstillinger)
- Hero-billede øverst
- Intro-tekst
- 3-kolonne grid med udstillingscards
- Sektion med demonstrationer/events

### Detailside (f.eks. Lyslabyrinten)
- Overskrift (H1) + underrubrik
- Meta-info bar (alder, fag, varighed) med ikoner
- Brødtekst
- Relaterede cards (3-kolonne: Guide, Videnskaben bag, Til læreren)
- Quiz/mobilspil-bannere

---

## 5. Tone og stil

### Billedstil
- Høj kvalitet, naturalistisk fotografering
- Børn i leg og eksperimenter
- Levende farver, ofte med videnskabeligt motiv (sæbebobler, lys, vand)
- Billedformat: typisk 16:9 til helte-billeder, ca. 387×217px til cards

### Teksttone
- Venlig, entusiastisk, inkluderende
- Fokus på "oplev", "udforsk", "leg", "bliv klogere"
- Korte, inviterende sætninger
- CTA-stil: "Køb billet", "Læs mere", "Se mere", "Tag quizzen"
- Sæsonbetonede hooks (ferier, festivaler)

### Overordnet æstetik
- Ren, moderne, videnskabelig
- Masser af luft og whitespace
- Mørk nav + lys krop + mørk footer
- Farverige accenter via tema-systemet
- Animerede hover-effekter (cubic-bezier transitions)
- Mobilvenlig (responsive breakpoints, off-canvas menu)

---

## 6. Teknisk stack

- **CMS:** WordPress (Yoast SEO, MaxMegaMenu, Boxzilla)
- **CSS Framework:** Foundation (12-kolonne grid)
- **jQuery:** 3.6.0 (via Cloudflare CDN)
- **Fonts:** Custom hosted (EXP-display, Mark Pro via Linotype/Monotype)
- **Analytics:** Google Tag Manager + Matomo
- **Billedoptimering:** PCO Picture plugin
