# Brief: AI-søgning på forsiden (mobil)

## Formål
Gøre søgning til en central del af forsideoplevelsen i stedet for et gemt ikon i headeren. Brugeren skal kunne udtrykke sin rejsedrøm i fritekst og få relevante, personlige resultater — med mulighed for at forfine via dialog.

Kun 1,74% bruger den nuværende søgning. Målet er at gøre søgning til det naturlige første skridt.

## Kontekst
Demoen viser en mobil forside for Profil Rejser. Søgefeltet erstatter ikke den eksisterende navigation, men tilføjer et nyt intent-baseret element mellem hero-sektionen og resten af forsideindholdet.

## Indhold og struktur

### Sektion 1: Hero (eksisterende)
- Fuldbredde billede med mørkt overlay
- "Beyond ordinary travel" som overskrift i Zahrah Light
- Kort undertekst

### Sektion 2: Søgefelt (nyt)
- Overskrift: **"Fortæl os om din drømmerejse ..."** (Zahrah Light)
- Inputfelt med placeholder-tekst: *"Nordbys, Mauritius eller Gourmet?"*
- SØG-knap (primær pill-knap, navy `#1A2C41`)
- Baggrund: lys `#F3F1ED` for at adskille fra heroen

### Sektion 3: Resten af forsiden (eksisterende)
- "Find inspiration til din næste rejse ..." og det øvrige forsideindhold fortsætter under søgefeltet

### Sektion 4: Resultatpanel (slide-up)
Aktiveres når brugeren trykker SØG. Panelet slider op fra bunden og overtager ca. 80% af skærmen. De øverste ~20% viser forsiden bag (dimmet).

**Panelets indhold fra top til bund:**

1. **Header-bar**
   - X-knap (luk) i højre hjørne
   - Eventuelt brugerens søgeterm som kontekst

2. **AI-introtekst**
   - Kort, personlig sætning i Profil Rejsers tone
   - Eksempel: *"Her er tre oplevelser der matcher din interesse for gourmet i Asien:"*

3. **Tre resultater** (tekstbaseret, kompakt)
   - Hver resultat: **Titel** (klikbar, navy) + manchettekst (1-2 linjer, grå)
   - Adskilt med subtil divider
   - Klik på et resultat åbner den pågældende side

4. **"Se flere"-knap**
   - Sekundær knap (outline-stil)
   - Loader flere resultater i samme format under de eksisterende

5. **Opfølgende spørgsmål-felt**
   - Inputfelt i bunden af panelet: *"Stil et opfølgende spørgsmål ..."*
   - Når brugeren sender et opfølgende spørgsmål, **erstattes** introteksten og resultaterne med et nyt svar og nye resultater
   - Den nye introtekst afspejler det forfinede scope, f.eks.: *"Her er tre street food-oplevelser i Asien:"*

## Specifikke krav

### Interaktioner
- Panel animerer op fra bunden (smooth slide, ~300ms ease-out)
- Baggrunden bag panelet dimmes med et mørkt overlay
- X-knap lukker panelet med omvendt animation
- "Se flere" loader resultater uden at resette panelet
- Opfølgende spørgsmål erstatter indhold (ingen chat-historik)

### Indhold i demoen
Brug realistisk indhold. Eksempel-scenarie:

**Første søgning:** "gourmet i Asien"
- Intro: "Her er tre oplevelser der matcher din interesse for gourmet i Asien:"
- Resultat 1: **"Kulinarisk rejse gennem Thailand"** — Oplev autentisk thai-køkken fra Bangkok's gadekøkkener til Chiang Mai's kokke-skoler.
- Resultat 2: **"Vietnam — fra pho til fine dining"** — En rejse gennem Vietnams madkultur, fra street food i Hanoi til Hoi An's fusionsrestauranter.
- Resultat 3: **"Japans gastronomiske skatkammer"** — Sushi i Tokyo, ramen i Osaka og sake-smagning i Kyoto.

**Opfølgende søgning:** "hvad med noget med street food?"
- Intro: "Her er tre street food-oplevelser i Asien:"
- Resultat 1: **"Street food-guide til Bangkok"** — De bedste markeder, gadekøkkener og lokale favoritter i Thailands hovedstad.
- Resultat 2: **"Hanois 10 bedste street food-oplevelser"** — Fra bun cha til egg coffee — en guide til Vietnams gastronomiske hjerte.
- Resultat 3: **"Night markets i Taipei"** — Taiwans berømte natmarkeder byder på alt fra stinky tofu til bubble tea.

### Responsive hensyn
- Kun mobil (max-width ~430px)
- Panelet skal have afrundede hjørner i toppen (border-radius ~16px)
- Inputfelt og knapper skal være touch-venlige (min. 44px høje)

## Designsystem-referencer

**Genbruges:**
- Farvepaletten (navy, hvid, lys baggrund, grå tekster)
- Zahrah Light til overskrifter
- DM Sans til brødtekst og UI
- Primær pill-knap til SØG
- Sekundær outline-knap til "Se flere"

**Nyt:**
- Slide-up panel (bottom sheet) med dimmet baggrund
- Kompakt resultatformat (titel + manchette, ingen billeder)
- Opfølgende spørgsmål-felt i panelbunden

## Succeskriterier
- Demoen viser en troværdig mobilforside med det nye søgefelt
- Man kan "trykke" SØG og se panelet slide op med resultater
- Man kan se et opfølgende spørgsmål erstatte resultaterne
- Det hele føles som en naturlig del af Profil Rejsers eksisterende designsystem
