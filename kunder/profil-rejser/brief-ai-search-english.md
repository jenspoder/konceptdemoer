# Brief: AI Search — English demo index

## Formål
Præsentere AI-søg-konceptet for internationale kolleger, der ikke læser dansk. Siden samler de to engelske AI-søg-demoer på én overskuelig landingsside — spejlet af den eksisterende danske `index.html`, men afgrænset til netop dette koncept.

## Kontekst
Der eksisterer allerede to danske AI-søg-demoer:
- **Mobil:** `demo/index-AI-demo1.html` (via `mobil-preview.html?side=AI-demo1`)
- **Desktop:** `demo/ai-soegning-desktop.html`

Opgaven er:
1. Oversætte begge demoer til engelsk (al synlig tekst, typewriter-placeholders, AI-svar, knapper, navigation)
2. Bygge en engelsk indeksside der samler dem

## Indhold og struktur

### Indeksside: `demo-ai-english/index.html`

Samme layout og visuelle stil som `kunder/profil-rejser/index.html`. Indhold:

- **Overskrift:** "Profil Rejser — AI Search Demo"
- **Undertitel:** "Interactive prototypes demonstrating an AI-powered search experience on the homepage."
- **Ét demo-group:** "Concept: AI Search on the Homepage" med beskrivelsen "An integrated search experience with AI-driven dialogue, inline results and expert CTA."
- **To links:**
  1. 📱 "Homepage with AI search" → `mobil-preview-en.html?side=AI-demo1-en` — *"Search field, slide-up panel, "Tell me more", follow-up questions"*
  2. 🖥️ "Homepage with AI search (Desktop)" → `demo-ai-english/ai-search-desktop.html` — *"Slide-over panel from the right, 5 results, follow-up questions"*

### Mobil iPhone-ramme: `mobil-preview-en.html`
Kopi af `mobil-preview.html` med al dansk UI-tekst oversat til engelsk. Loader `demo-ai-english/ai-search-mobile.html` når `?side=AI-demo1-en`.

### Mobil demo: `demo-ai-english/ai-search-mobile.html`
Engelsk version af `demo/index-AI-demo1.html`. Oversæt:
- Header: "PROFIL REJSER" (beholdes), navigation links → "Destinations", "Theme Trips", "About Us", "My Account"; CTA-knap → "Call us"
- Hero headline → "Discover your next journey" (eller tilsvarende poetisk engelsk i Playfair-stilen)
- Hero subtext → "Tell us what you're looking for — we'll find the perfect trip for you."
- AI-søgefelt label/overskrift → "What kind of trip are you looking for?"
- AI-intro undertekst → "Our AI finds the right journey for you — personally curated by our travel experts."
- Typewriter-placeholders (samme idé, på engelsk):
  - "A family trip to Southeast Asia in July…"
  - "Something adventurous with hiking and culture…"
  - "A romantic getaway, ideally with a private beach…"
  - "Two weeks in South America, off the beaten track…"
- SØG-knap → "SEARCH"
- Slide-up panel: alle AI-svar, rejseforslag, knapper og opfølgende spørgsmål oversættes naturligt til engelsk. Bevar tonen — varm, ekspertdrevet, personlig.
- "Fortæl mig mere" → "Tell me more"
- Opfølgende spørgsmål → engelske varianter med samme tema (familie, romantik, eventyr, budget)

### Desktop demo: `demo-ai-english/ai-search-desktop.html`
Engelsk version af `demo/ai-soegning-desktop.html`. Oversæt på samme måde:
- Navigation → "Destinations", "Theme Trips", "Group Travel", "About Us"; "Contact us"
- Hero → "Find your perfect journey" / "Our travel experts create tailor-made trips — just for you."
- Søgesektion overskrift → "What kind of trip are you dreaming of?"
- AI-intro → "Describe your ideal trip and our AI will find matching journeys — curated by our experts."
- Typewriter-placeholders: samme engelske sæt som mobil
- SØGE-knap → "SEARCH"
- Slide-over panel: alle AI-svar, rejsekort, knapper og opfølgende spørgsmål på engelsk
- "Fortæl mig mere" → "Tell me more"
- Inspiration-sektion under søgning → "Popular destinations", kort-labels, priser osv. på engelsk

## Specifikke krav
- Al tekst der er synlig for brugeren oversættes — inkl. aria-labels og title-attributter hvis de har meningsfuldt indhold
- `lang`-attributten på `<html>` sættes til `en`
- `<title>` → "Profil Rejser — AI Search Demo"
- Tonen skal være varm og premium — ikke generisk tech-sprog. Bevar den poetiske, rejse-inspirerende stemning fra originalen
- Brug realistiske engelske rejseforslag i AI-svarene (Thailand, Japan, Peru, Maldives osv.) — ikke oversatte navne fra de danske forslag
- Ingen lorem ipsum

## Fil-struktur der skal oprettes
```
kunder/profil-rejser/
  demo-ai-english/
    index.html            ← engelsk indeksside (spejler index.html men kun AI-søg)
    ai-search-mobile.html ← engelsk mobil demo
    ai-search-desktop.html← engelsk desktop demo
  mobil-preview-en.html   ← engelsk iPhone-ramme
```

## Designsystem-referencer
- Genbruger alle eksisterende CSS-variabler og typografi fra originaldemoerne (copy-paste stilark)
- Ingen nye komponenter — kun tekstoversættelse og evt. trivielle justeringer af tekst-bredde

## Succeskriterier
- En international kollega kan åbne `demo-ai-english/index.html` og navigere til begge demoer uden at støde på dansk tekst
- Stemningen og kvaliteten af AI-dialogen føles naturlig på engelsk — ikke som en direkte oversættelse
- Siden ser visuelt identisk ud med de danske versioner
