# Designsystem — Sjællandske Nyheder (sn.dk)

Dokumenteret af Design Systems Dokumentarist, april 2026.
Baseret på kildekode-analyse af sn.dk (WordPress-tema `sn`, bygget med custom plugins).

---

## Visuel identitet

### Farvepalet

Sitet definerer farver som CSS-variabler i `:root` — de hedder `--color-1` til `--color-13` og er tilknyttet semantiske aliasser.

#### Tema-farver (fra inline `:root`)
| Variabel | Hex | Rolle |
|---|---|---|
| `--color-1` | `#000000` | Primær tekst / accent |
| `--color-5` | `#efefef` | Lys baggrund (sektioner) |
| `--color-6` | `#f0f9fc` | Meget lys blå baggrund |
| `--color-7` | `#f8f8f8` | Alternativ grå baggrund |
| `--color-8` | `#ffffff` | Hvid |
| `--color-9` | `#ffdd45` | Gul accent (breaking-mærker?) |
| `--color-10` | `#ef2c52` | Rød (breaking, alarm) |
| `--color-11` | `#00a0e4` | Blå (links, CTA) |
| `--color-12` | `#c75e38` | Orange/terrakotta |

#### Semantiske farver (fra `base.min.css`)
| Variabel | Hex | Rolle |
|---|---|---|
| `--color-blue-light` | `#0076da` | Primær knap- og link-farve |
| `--color-blue-lighter` | `#0058a2` | Hover-tilstand, blå |
| `--color-separator` | `#d7d7d7` | Skillelinjer |
| `--color-card-alt-bg` | `#f4f2ef` | Alternativ kortbaggrund |
| `--color-sponsored-bg` | `#f9f7f3` | Sponsoret indhold |
| `--color-breaking-border` | `#f3c700` | Breaking-ramme (gul) |
| `--color-live-bg` | `#dc2626` | Live-tag baggrund (rød) |
| `--color-muted-foreground` | `#71717a` | Nedtonet tekst |
| `--color-gray-light` | `#f4f4f5` | Lys grå |
| `--color-gray-light-border` | `#d1d5db` | Border-farve |

**Dominerende farver i praksis:** Sort tekst på hvid/lys grå baggrund. Blå (#0076da) som primær interaktionsfarve. Rød (#dc2626 / #ef2c52) til breaking og live. Sort er også primær accent — sitet er meget monokromt med blå som eneste stærke farve.

---

### Typografi

**To skrifttyper:**

| Font | Variabel | Brug |
|---|---|---|
| **Inter** (variable, 100–900) | `--main-font-family` | Brødtekst, UI, navigation, meta |
| **Source Serif 4** (serif) | `--secondary-font-family` | Overskrifter (h1 på artikler) |

Inter bruges til alt UI; Source Serif 4 bruges primært til store artikel-overskrifter (H1). Begge fonts serveres lokalt fra WordPress-temaet.

#### Størrelser (base: 16px)

| Token | rem | px | Brug |
|---|---|---|---|
| `--font-size-xsmall` | 0.75rem | 12px | Etiketter, meta-data |
| `--font-size-small` | 0.875rem | 14px | Caption, byline |
| `--font-size-normal` | 1rem | 16px | Brødtekst, liste-teasers |
| `--font-size-medium` | 1.125rem | 18px | H2, manchet-varianter, knapper |
| `--font-size-large` | 1.25rem | 20px | Block-1, widget |
| `--font-size-excerpt` | 1.375rem | 22px | Manchet desktop |
| `--font-size-excerpt-mobile` | 1rem | 16px | Manchet mobil |
| `--font-size-h1` | 4rem | 64px | Artikel H1 desktop |
| `--font-size-h1-laptop` | 3rem | 48px | Artikel H1 laptop |
| `--font-size-h1-tablet` | 2.5rem | 40px | Artikel H1 tablet |
| `--font-size-h1-mobile` | 2rem | 32px | Artikel H1 mobil |
| `--font-size-h2` | 1.125rem | 18px | H2 |
| `--font-size-h3`–`h6` | 1rem | 16px | H3–H6 |
| `--font-size-meta-header` | 0.6875rem | 11px | Sektion-labels, kategori |
| `--font-size-widget-title` | 1.5rem | 24px | Sektionsoverskrifter |
| `--font-size-page-h1` | 2.625rem | 42px | Indholdssider (ikke artikel) |

#### Linjehøjder
- Brødtekst: 1.556
- Manchet: 1.727 (desktop) / 1.556 (mobil)
- H1: 1.156 (desktop)

#### Skriftvægte
Inter er en variable font — alle vægte 100–900 er tilgængelige via `font-weight`. Systemet bruger:
- Regular (400), Medium (500), Semibold (600), Bold (700), Extra-bold (800)

---

### Spacing-system

Fast skala i 10px-trin:

| Token | Værdi |
|---|---|
| `--spacing-gutter` | 15px |
| `--spacing-1` | 10px |
| `--spacing-2` | 20px |
| `--spacing-3` | 30px |
| `--spacing-4` | 40px |
| `--spacing-5` | 50px |
| `--spacing-6` | 60px |
| `--spacing-7` | 70px |
| `--spacing-8` | 80px |

Grid-gutter kolonne/række: `2rem` (32px).

### Layout & grid
- Max-bredde (listesider): **1035px**
- Max-bredde (artikelindhold): **964px**
- Max-bredde (popout/panel): **375px**
- Grid-kolonne-bredde: **300px**
- Border-radius: **4px** (meget lille — sitet er næsten firkantet)

---

## Komponenter

### Navigation / Header

**Struktur:** `<header id="header" class="site-header site-header--main">`

- Statisk top-bar (`header--static-top`) med utilty-links
- To rækker: `header-row-first` (logo + søg + utility) og en sekundær navigationslinje
- **Hamburger/drawer** på mobil: `menu-drawer` med klassen `header-menu-drawer` — skubber ind fra siden
- Primær navigation (desktop): `nav.nav-menu-drawer-third` med dropdown-hierarki

**Navigationspunkter:**
- **Område** (dropdown): Midtsjælland, Nordsjælland, Vestsjælland, Sydsjælland, Lolland-Falster, Møn, Bornholm — med kommuner underneden
- **Emne**: 112, Debat, Erhverv, Kultur, Podcast, Sport
- **Erhverv**, **Debat**, **Dødsannoncer**

**Utility (højre side):** Log ind, Køb abonnement, Selvbetjening, Søg

**CSS-klasser:** `.menu__item`, `.menu__link`, `.menu-drawer-third__item`, `.menu-drawer-third__sub-menu`

---

### Knapper

Primær knap-stil:
```css
background: #0076da;
color: #fff;
border-radius: 0;          /* ingen afrunding */
font-family: Inter;
font-size: 1.125rem (18px);
font-weight: 500;
min-height: 55px;
width: 290–300px;
padding: 1rem;
transition: all .15s ease-in-out;
hover: opacity 0.95;
```

Knapper er **rektangulære** (border-radius: 0) — usædvanligt og karakteristisk for sitet. Bredde er fast (290–300px), ikke fluid.

**Varianter:**
- Primær blå: `--base-button-color` (#0076da), hvid tekst
- `.btn--blue`: blå tekst (outline-lignende)
- `.btn--green`: grøn tekst (`--color-11` / #00a0e4)

---

### Artikelkort / Teasers

Serveret via plugin `sn-theme-teaser`. Kortbaggrunde:
- Standard: hvid (#fff)
- Alt: `--color-card-alt-bg` (#f4f2ef)
- Sponsoreret: `--color-sponsored-bg` (#f9f7f3) med blå label (#0076da)
- Shadow: `0 8px 16px 0 rgba(0,0,0,.2)`

**Teaser-elementer:**
- Kategori-label (lille caps, 11px Inter)
- Overskrift (Inter bold, 1–1.25rem)
- Manchet/excerpt (Inter regular, 1.375rem desktop)
- Billede (3:2 eller 16:9 format typisk)
- Byline / dato (Inter small, 14px)
- Betalingsmur-markering: lås-ikon via `icon-lock` (custom sn-icons font)
- Breaking-markering: gul kant (#f3c700)
- Live-markering: rød pulserende dot (#dc2626)

---

### Artikelside

**Overskrift (H1):**
- Font: Source Serif 4, 4rem desktop → 2rem mobil
- Linjehøjde: 1.156

**Manchet:**
- Font: Inter, 1.375rem (22px), linjehøjde 1.727

**Brødtekst:**
- Font: Inter regular, 1rem, linjehøjde 1.556
- Max-bredde: 964px

**Citat/blockquote:**
- Font: Source Serif 4 italic, 1.75rem
- Linjehøjde: 2.5rem
- Dekorativt citationstegn via sn-icons

**Meta (byline, dato):**
- Font: Inter, 0.875rem (14px)

---

### Formularer

- Labels: Inter, 0.75rem (12px)
- Input-felter: standard browser, sandsynligvis med `border: 1px solid #d1d5db`
- Submit-knap: primær blå knap (se knapper)
- Gravity Forms bruges til redaktionelle formularer

---

### Footer

- Klasse: `.site-footer`
- Mørk baggrund (sandsynligvis `--color-1` / sort eller mørkeblå)
- Font: Inter, `--font-family-footer`
- Indhold: kontaktoplysninger, sociale medier (Facebook, Instagram, Twitter/X, LinkedIn), juridiske links, Pressenævnet-mærke

---

## Sidetyper

### 1. Forside / Nyhedsoverblik
Fast sektion-layout med JavaScript-renderede blokke:
- "Nyheder fra mit område" (lokaliseret)
- "Abonnenternes favoritter"
- "Redaktionen anbefaler"
- "Debat"
- "Leder"
- "Video"
- Breaking-sektion (gul kant, rød tekst)

### 2. Sektionsside (kommune/region)
F.eks. `/slagelse/` — samme layout som forsiden men filtreret:
- "Nyhedsoverblik: [Sted]"
- "Døgnrapport", "Lokal debat", "Butiksliv", "Bolighandel"
- Sektions-specifik navigation øverst

### 3. Artikelside
- Hero-billede (fuld bredde)
- H1 (Source Serif 4, stor)
- Manchet
- Byline + dato + deleknapper (Facebook, Twitter, LinkedIn, email, print)
- Brødtekst i max 964px
- Betalingsmur for abonnenter
- Relaterede artikler i bunden

### 4. Debatside
- Indlæg-liste med forfatternavne fremhævet
- Lignende kortstruktur som nyheder

### 5. Emnesider (sport, erhverv, kultur)
- Samme grid-layout som sektionssider
- Topnavigation med emne-filtre

---

## Tone og stil

**Billedstil:**
- Redaktionelle nyhedsfoto — dokumentarisk, ikke poleret
- Billeder spiller en sekundær rolle ift. tekst (nyhedssite)
- Ingen stiliserede illustrationer

**Teksttone:**
- Saglig og direkte — klassisk journalistisk
- Overskrifter er korte og faktuelle
- CTA'er er simple: "Køb abonnement", "Log ind", "Læs mere"
- Lokalt fokus — kommunenavne og stednavn bruges aktivt

**Overordnet æstetik:**
Funktionel og informationstæt. Meget sort/hvid med blå som eneste markante farve. Ingen bløde kurver (border-radius: 4px). Nyhedsavisen som forbillede snarere end et moderne brand-site. Sitet er bygget til høj informationstæthed og hurtig scanning.
