# Brief: Optimeret CTA-struktur (4 demo-sider, mobil)

## Formål
Demonstrere en ny CTA-struktur hvor personlig kontakt (telefon) er primær konverteringsvej tidligt i brugerrejsen, og formularen først træder i karakter når brugeren har opbygget kontekst. Telefonisk dialog konverterer 50% til køb mod formularens 10% — men er i dag reelt usynlig på sitet.

## Kontekst
Fire mobilsider der viser CTA-strukturen på hvert niveau i brugerrejsen. Alle sider deler en sticky mobilbar i bunden, men indholdet i baren og det panel den åbner skifter efter niveau. Demoerne skal IKKE overskrive AI-søgning-demoen.

## Fælles element: Sticky mobilbar

Vises på alle fire sider. Popper op fra bunden efter 5 sekunder med en smooth animation.

**Visuelt:**
- Fast i bunden af skærmen
- Hvid baggrund med let skygge opad
- Venstre: Rundt portræt af rejseekspert (48px diameter)
- Midte: CTA-tekst (DM Sans, bold)
- Højre: Pil eller chevron
- Hele baren er klikbar
- Høj nok til at være touch-venlig (min. 60px)

**CTA-tekst skifter efter niveau:**

| Side | CTA-tekst |
|------|-----------|
| 01 Forside | "Ring og hør om mulighederne" |
| 02 Find destination | "Ring og hør om mulighederne" |
| 03 Thailand | "Tal med vores Thailand-ekspert" |
| 04 Konkret rejse | "Få et tilbud på denne rejse" |

---

## Side 1: Forside (`01-forside.html`)

### Sidestruktur
- **Hero:** Fuldbredde billede med overlay, "Beyond ordinary travel", undertekst
- **Destinationskort:** 3 kort (Maldiverne, Thailand, Grønland) i vertikal stack
- **Sticky mobilbar** popper op efter 5 sek.

### Sticky bar klik → "Ring-panel"
Slide-up panel (som AI-søgning-demoen), overtager ~60% af skærmen:
- Afrundede hjørner i top, handle-bar
- X-knap til at lukke
- **Overskrift:** "Ring og hør om mulighederne" (Zahrah Light)
- **Beskrivelse:** "Vores rejseeksperter hjælper dig med at finde den perfekte rejse — uanset om du drømmer om strand, kultur eller eventyr."
- **Telefonnummer:** "+45 77 33 55 00" — stort, tydeligt, klikbart (men inaktivt i demo)
- **Åbningstider:** "Man-fre 9-17, lør 10-14"
- Ingen formular på dette niveau

---

## Side 2: Find destination (`02-find-destination.html`)

### Sidestruktur
Baseret på den eksisterende side:
- **Hero:** Billede med "Vælg dit næste eventyr"
- **Regionskort:** Grupper af destinationskort under regionsoverskrifter:
  - "Asien" med 3-4 kort (Thailand, Vietnam, Japan, Bali)
  - "Det Indiske Ocean" med 2-3 kort (Maldiverne, Mauritius, Sri Lanka)
  - Vis mindst to regioner for at demonstrere layoutet
- Hvert kort: Landskabsbillede med destinationsnavn som overlay-tekst
- **Sticky mobilbar** popper op efter 5 sek.

### Sticky bar klik → "Ring-panel"
Identisk med forsiden — samme panel, samme indhold.

---

## Side 3: Destinationsside — Thailand (`03-thailand.html`)

### Sidestruktur
- **Hero:** Thailand-billede med overlay, "Rejser til Thailand"
- **Introduktionstekst:** 2-3 linjer om Thailand

- **EKSPERT-KORT (nyt, højt placeret):**
  - Baggrund: `#F3F1ED`
  - Foto af Alice (rundt, 80px)
  - **Navn:** "Alice Hamurkesen"
  - **Titel:** "12 års erfaring med Sydøstasien"
  - **Primær CTA:** "Ring til Alice: 77 33 55 00" (knap, navy pill)
  - **Sekundær CTA:** "Skriv til Alice om din rejse til Thailand" (outline-knap)

- **Rejseforslag:** 3 rejsekort:
  - "Kultur, boutique-hoteller og strand" — fra 22.720 kr., 15 dage
  - "På sporet af det autentiske Thailand" — fra 69.050 kr., 12 dage
  - "Nordthailand, Bangkok og strandferie" — fra 25.450 kr., 15 dage
  - Hvert kort: Billedbaggrund, titel, pris, varighed

- **GENTAGET CTA (kompakt, nyt):**
  - Mellem rejseforslag 3 og 4 (eller efter de 3)
  - Lys baggrund, kompakt layout
  - Tekst: "Har du brug for hjælp til at vælge?"
  - **CTA:** "Alice kender Thailand — ring og få en snak" (navy pill-knap)

- **Flere rejseforslag:** 3 mere:
  - "Bangkok, Uthai Thani og Phuket" — fra 21.530 kr.
  - "Romantik for to i Krabi og på Koh Lanta" — fra 17.175 kr.
  - "Bangkok, Chanthaburi og Koh Samet" — fra 26.320 kr.

- **Sticky mobilbar:** "Tal med vores Thailand-ekspert", popper op efter 5 sek.

### Sticky bar klik → "Ekspert-panel"
Slide-up panel, ~70% af skærmen:
- Handle-bar, X-knap
- **Foto af Alice** (stort, rundt, 96px)
- **Navn:** "Alice Hamurkesen"
- **Titel:** "Rejseekspert for Asien og Det Indiske Ocean"
- **Primær CTA:** "Ring til Alice: 77 33 55 00" (navy pill, stort)
- **Divider**
- **Eller skriv til Alice:**
- Kort formular: Navn, e-mail/telefon, fritekst ("Fortæl kort hvad du drømmer om")
- Send-knap

---

## Side 4: Konkret rejseside (`04-rejse.html`)

### Sidestruktur
Baseret på "Kultur, boutique-hoteller og strand":
- **Hero:** Rejsebillede med overlay, "Kultur, boutique-hoteller og strand"
- **Rejseinfo:** "15 dage / 12 nætter · Fra 22.720 kr."
- **Introduktionstekst:** 3-4 linjer om rejsen
- **Højdepunkter:** 4 korte bullet points (boutique-hoteller, tog/templer, kunsthåndværk, strand)
- **Rejseprogram:** 3-4 dage vist som accordion (dag 1, dag 2-3, dag 4-7, dag 8-15). Kun overskrifter — ikke fuldt indhold.
- **Prissektion:** "Fra 22.720 kr. pr. person"
- **Sticky mobilbar:** "Få et tilbud på denne rejse", popper op efter 5 sek.

### Sticky bar klik → "Tilbuds-panel"
Slide-up panel, ~80% af skærmen:
- Handle-bar, X-knap

**Toppen: Ekspert**
- Foto af Alice (rundt, 80px)
- "Alice er din ekspert på denne rejse"
- **Primær CTA:** "Ring til Alice: 77 33 55 00" (navy pill)

**Divider med tekst:** "Eller send en forespørgsel"

**Pre-udfyldt label:**
- Lys baggrund (`#F3F1ED`), border-radius
- "Din forespørgsel om:" + **"Kultur, boutique-hoteller og strand"** (bold)
- Lille "Skift"-link i højre side

**Formular (kompakt, 3 felter):**
- Navn
- Telefon eller e-mail
- Fritekst: "Fortæl os kort om dine ønsker" (textarea, 3 linjer)
- Send-knap (navy pill, fuld bredde)

---

## Specifikke krav

### Interaktioner
- Sticky bar: Slide-up animation efter 5 sekunder, smooth (300ms ease-out)
- Panels: Slide-up fra bunden som i AI-søgning-demoen
- Dimmet overlay bag panels
- X-knap og overlay-klik lukker panels
- Accordion i rejseprogrammet: Klik folder ud/ind
- Alle telefonnumre og formular-sends er inaktive (kun demo)

### Indhold
- Brug realistisk indhold fra det eksisterende site
- Ekspert: Alice Hamurkesen, Asien og Det Indiske Ocean
- Billeder: Unsplash rejsebilleder med korrekte proportioner
- Priser og varigheder fra de rigtige rejser

### Responsive
- Kun mobil (max-width ~430px)
- Touch-venlige elementer (min. 44px)
- Safe-area-inset for sticky bar

## Designsystem-referencer

**Genbruges:**
- Farvepalet (navy `#1A2C41`, hvid, lys baggrund `#F3F1ED`, grå tekster, guld `#9F8974`)
- Zahrah Light (Playfair Display som stand-in) til overskrifter
- DM Sans til brødtekst og UI
- Pill-knapper (navy primær, outline sekundær)
- Destinationskort med billedoverlay
- Slide-up panel-mønster fra AI-søgning-demoen

**Nyt:**
- Sticky mobilbar med ekspertportræt
- Ekspert-kort (stor og kompakt variant)
- Pre-udfyldt kontekst-label på formular

## Succeskriterier
- Fire sider der tydeligt viser progressionen i CTA-strukturen
- Sticky bar skifter tekst og panelindhold naturligt mellem niveauerne
- Ekspert-kort føles som en naturlig del af designsystemet
- Formularside med pre-udfyldt kontekst virker overbevisende
- Det hele kan vises til kunden som et sammenhængende koncept
