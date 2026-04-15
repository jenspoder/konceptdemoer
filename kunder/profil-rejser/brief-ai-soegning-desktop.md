# Brief: AI-søgning på forsiden (desktop)

## Formål
Demoen viser hvordan Profil Rejsers AI-søgning kan fungere på forsiden i desktop-visning. Løsningen erstatter den eksisterende Raffle.ai-søgning og bygger direkte videre på den eksisterende mobil-demo (`demo/index-AI-demo1.html`).

Målgruppen er den samme: rejselystne besøgende der lander på forsiden og vil udforske destinationer eller rejsetyper.

## Kontekst
Mobilversionen af AI-søgningen er allerede bygget som en selvstændig demo. Den bruger et bottom sheet-panel der slider op nedefra. Desktop-versionen skal have **identisk indhold og flow**, men tilpasse præsentationen til den ekstra plads.

Desktop-menuen på profil-rejser.dk (se screenshot i sparring) er reference-designet for panelet: den slider ind fra højre, dækker ca. 2/3 af skærmen, med hvid baggrund og forsiden synlig bagved i venstre side.

## Indhold og struktur

### Forsiden (bagved panelet)
Siden er en desktop-version af den eksisterende mobil-demo-forside:

1. **Header** — Profil Rejser-logo, desktop-navigation (Find destination, Find krydstogt, Firmarejser), "Få et tilbud"-CTA. Ingen separat søgeknap i headeren (AI-søgningen erstatter Raffle.ai).
2. **Hero** — Fuldbredde billede med overlay, overskrift "Beyond ordinary travel", undertekst.
3. **Søgesektion** — Placeret lige under hero'en (som på mobilen). Overskrift: "Fortæl os om din drømmerejse ...". Inputfelt + SØG-knap. Feltet har forudfyldt tekst: "gourmet i Asien".
4. **Inspirationskort** — Destinationskort (Maldiverne, Thailand, Grønland) i et grid tilpasset desktop (3 kolonner).
5. **Footer** — Standard Profil Rejser footer.

### Søgeresultat-panel (slide-over fra højre)
Åbner når brugeren klikker SØG eller trykker Enter. Panelet slider ind fra højre side, i stil med desktop-menuen:

- **Bredde:** Ca. 2/3 af viewport-bredden (matcher menuen)
- **Baggrund:** Hvid (`#FFFFFF`)
- **Animation:** Slider ind fra højre med en blød cubic-bezier transition (som menuen)
- **Overlay:** Intet mørkt overlay — forsiden forbliver synlig bagved i venstre side
- **Luk:** Luk-knap (×) øverst til højre + klik udenfor panelet lukker det + Escape-tast

**Panelet indeholder (identisk med mobilversionen):**

1. **Søgeforespørgsel** — Viser hvad brugeren søgte på: `Søgning: "gourmet i Asien"`
2. **Intro-tekst** — "Her er fem oplevelser der matcher din interesse for gourmet i Asien:"
3. **5 søgeresultater** — Titel + beskrivelse for hver. Fade-in animation. (Mobilen viser 3, desktop viser 5 fordi der er plads — men det er de samme resultater, blot at desktop viser de første 5 med det samme i stedet for 3 + "Se flere")
4. **Handlingsknapper** — "Se flere" og "Fortæl mig mere" (pill-buttons)
5. **"Se flere"** → viser yderligere resultater + rejseekspert-CTA
6. **"Fortæl mig mere"** → typing-indicator → AI-prosatekst → rejseekspert-CTA
7. **Rejseekspert-CTA** — Alice Hamurkesen med foto, "Ring til Alice"-knap, mail-ikon (identisk med mobilen)
8. **Opfølgende spørgsmål** — Inputfelt i bunden af panelet: "Stil et opfølgende spørgsmål ..." + send-knap. Trigger nyt svar i samme panel.

### Interaktionsflow (identisk med mobilen)
1. Bruger skriver søgning → klikker SØG
2. Panel slider ind → typing-indicator → 5 resultater + handlingsknapper fader ind
3. Bruger klikker "Se flere" → flere resultater + ekspert-CTA
4. ELLER bruger klikker "Fortæl mig mere" → AI-prosatekst + ekspert-CTA
5. Bruger kan skrive opfølgende spørgsmål → nyt svar i panelet
6. Bruger lukker panelet → slider ud til højre

## Specifikke krav

### Responsivt
- Demoen er kun desktop (min-width ca. 1024px). Mobilversionen eksisterer allerede som separat demo.
- Panelet skal ikke skubbe forsideindholdet — det lægger sig ovenpå (som menuen).

### Indhold
- **Samme data og tekster** som mobilversionen. Ingen nyt indhold.
- Eneste forskel: 5 initiale resultater i stedet for 3 (brug de 3 eksisterende + de første 2 fra `extra`-arrayet).
- Intro-teksten opdateres tilsvarende: "fem oplevelser" i stedet for "tre oplevelser".

### Animation og timing
- Panel slide-in: `cubic-bezier(0.32, 0.72, 0, 1)` — samme som mobilens bottom sheet
- Typing-indicator: 1.2s før resultater vises
- Fade-in på resultater: staggered med 0.1s delay pr. element
- Panelet skal have smooth scroll for langt indhold

### Design
- Brug designsystemets farver, typografi og knapper (se `designsystem.md`)
- Panelet følger desktop-menuens visuelle mønster: hvid baggrund, ingen overlay, ca. 2/3 bredde
- Luk-knap: cirkulær, `#F3F1ED` baggrund, × ikon (som i mobilversionen)

## Designsystem-referencer

### Eksisterende komponenter der genbruges
- Header (desktop-variant fra `05-thailand-desktop.html`)
- Hero-sektion (desktop-variant)
- Søgefelt og SØG-knap (fra mobil-demoen, tilpasset bredde)
- Resultat-items (`.result-item` fra mobil-demoen)
- Handlingsknapper (`.action-btn` pill-buttons)
- Rejseekspert-CTA (`.expert-cta` fra mobil-demoen)
- Opfølgningsfelt (`.followup-field` fra mobil-demoen)
- Typing-indicator og fade-in animationer

### Nye komponenter
- **Slide-over panel** — nyt panel-design der matcher desktop-menuens mønster (slide fra højre, 2/3 bredde, hvid baggrund, ingen overlay). Erstatter mobilens bottom sheet.

## Succeskriterier
- Panelet føles som en naturlig del af profil-rejser.dk's desktop-oplevelse — det matcher menuens visuelle sprog
- Identisk indhold og flow som mobilversionen (bortset fra 5 vs. 3 initiale resultater)
- Søgeresultater vises hurtigt (før AI-svaret) — den centrale pointe i konceptet
- Alle interaktioner virker: søg, se flere, fortæl mig mere, opfølgende spørgsmål, luk panel
- En demo man kan åbne i en browser og præsentere for kunden
