# Brief: Iscenesættelse af AI-søgning på forsiden

## Formål
AI-søgefeltet på forsiden (både mobil og desktop) virker i dag som et almindeligt søgefelt. Målet er at iscenesætte det tydeligere, så besøgende øjeblikkeligt forstår at:
1. Dette er ny, AI-drevet søgning — ikke klassisk keyword-søgning
2. Man må skrive frit: stemning, budget, vejr, aktiviteter, rejsetype

To konkrete greb skal implementeres: **animeret typewriter-placeholder** og **AI-intro-linje over feltet**.

## Kontekst
- Opdaterer eksisterende demoer:
  - Mobil: `kunder/profil-rejser/demo/index-AI-demo1.html`
  - Desktop: `kunder/profil-rejser/demo/ai-soegning-desktop.html`
- Søgesektionen ligger allerede under heroen med overskriften *"Fortæl os om din drømmerejse ..."* og et inputfelt med SØG-knap.
- Begge demoer skal opdateres synkront — samme iscenesættelse, tilpasset hvert format.

## Indhold og struktur

### 1. AI-intro-linje (ny, over overskriften)
En lille label/pill placeret **over** `<h2>"Fortæl os om din drømmerejse ..."</h2>`.

- **Tekst:** `Ny · Spørg som du ville spørge en rejseven`
- Indeholder et lille ikon/symbol til venstre — brug en simpel ✨ eller en lille stiliseret SVG-stjerne (ingen emoji hvis det kan undgås — helst inline SVG i accent-guld `#9F8974`).
- **Typografi:** DM Sans, 13px, letter-spacing `0.08em`, uppercase eller sentence case — vælg det der passer bedst visuelt til Profil Rejsers eksisterende labels.
- **Farve:** Navy `#1A2C41` tekst. Guld `#9F8974` ikon. Eller subtil baggrundspill i `#FFFFFF` med 1px border i `rgba(26,44,65,0.12)` og 9999px border-radius.
- **Margin:** 0 0 12px 0 (mellem intro-linjen og overskriften)
- **Placering:** Centreret på både mobil og desktop (matcher overskriften).

### 2. Animeret typewriter-placeholder (opdatering af eksisterende input)
Erstatter den statiske `placeholder="Nordlys, Mauritius eller Gourmet?"`.

**Adfærd:**
- Når siden loader og feltet er tomt, cykler placeholderen gennem en liste af eksempler med typewriter-effekt.
- Hver sætning skrives bogstav-for-bogstav, pauser kort (ca. 1.5s), slettes igen bogstav-for-bogstav, og den næste skrives.
- Stopper øjeblikkeligt hvis brugeren fokuserer feltet eller begynder at skrive.
- Genstarter hvis brugeren rømmer feltet og mister fokus.

**Sætninger (brug disse, i rækkefølge):**
1. `Gourmet i Asien ...`
2. `Solferie med børn i efterårsferien ...`
3. `Et roligt sted uden turister ...`
4. `Bryllupsrejse til et paradis ...`
5. `Storbyferie med god mad og kultur ...`

**Timing:**
- Typing-hastighed: 45-60ms pr. bogstav
- Pause efter fuld sætning: 1500ms
- Slette-hastighed: 25-35ms pr. bogstav
- Pause mellem sætninger: 400ms

**Teknisk note:**
- Da `<input>`-elementer ikke kan animere placeholder direkte, skal det implementeres som en pseudo-placeholder: et `<span>`/`<div>` absolut-positioneret inde i inputfeltets wrapper, der viser teksten når `input.value === ""`. Den rigtige `placeholder`-attribut fjernes (eller sættes til `""`) når JS er aktiv, så der ikke er dobbeltvisning.
- Sørg for at pseudo-placeholderen har samme font, størrelse, farve (`#999`) og padding som det faktiske inputfelt.
- Skjul pseudo-placeholderen så snart `input.value !== ""` eller feltet er i fokus.

**Demo-fodnote:** Desktop-demoen har i dag `value="gourmet i Asien"` forudfyldt. Fjern denne `value` så typewriter-effekten kan vises fra start. (Søgningen kan stadig trigges manuelt.)

## Specifikke krav

### Interaktioner
- Typewriter starter når DOM er klar.
- Focus på inputfeltet → pseudo-placeholder fjernes øjeblikkeligt, animationen pauses.
- Blur med tomt felt → animationen genstarter fra næste sætning i listen.
- Animationen må aldrig forstyrre brugerens input.
- Respect `prefers-reduced-motion`: hvis brugeren har reduceret bevægelse aktiveret, vises blot den første sætning statisk som placeholder (ingen animation).

### Responsivt
- Intro-linjen skal bryde pænt på små skærme — ingen tekst-overflow.
- Typewriter-placeholder må ikke skabe layout shift: wrapper skal have stabil højde.

### Indhold
- Brug sætningerne ovenfor som de er — de er valgt til at demonstrere spændvidden i AI-søgningen.

## Designsystem-referencer

**Genbruges:**
- Farvepalet: navy `#1A2C41`, guld `#9F8974`, lys baggrund `#F3F1ED`, grå `#999`
- DM Sans til intro-linjen
- Pseudo-placeholder matcher eksisterende `.search-input::placeholder`-stil

**Nyt:**
- Intro-linje-komponent (pill eller bare tekst+ikon) over søgeoverskriften
- Typewriter-placeholder-mekanik (JS + DOM-element)

## Succeskriterier
- Man åbner mobil-demoen og desktop-demoen og ser tydeligt at søgefeltet er AI-drevet, før man overhovedet har klikket.
- Placeholderen animerer flydende gennem alle 5 sætninger uden stutter eller layout shift.
- Animationen stopper øjeblikkeligt når man klikker i feltet.
- Intro-linjen ser ud som en naturlig del af Profil Rejsers designsystem — ikke et fremmedlegeme.
- Fungerer identisk på mobil (430px wrapper) og desktop (fuld bredde).
