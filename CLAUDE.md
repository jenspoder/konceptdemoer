# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Formål

Dette projekt er en arbejdsproces til at lave demo-koncepter til eksisterende kunders websites. Processen har tre faser, hver med sin egen agent-rolle:

1. **Design Systems Dokumentarist** (`agenter/01-design-dokumentarist.md`) — Analyserer et eksisterende site og dokumenterer designsystemet
2. **Kreativ UX Sparringspartner** (`agenter/02-ux-sparringspartner.md`) — Sparrer om nye koncepter og producerer et brief
3. **Frontend-udvikler** (`agenter/03-frontend-udvikler.md`) — Bygger demo-sider baseret på brief og designsystem

## Sådan bruges det

### Start en fase
Sig f.eks.: *"Kør som Design Systems Dokumentarist for kunden Profil Rejser"* — Claude vil så følge instruktionerne i den pågældende agent-fil.

### Kundemapper
Hver kunde får sin egen mappe under `kunder/`. Outputtet fra hver fase gemmes her:

```
kunder/<kundenavn>/
  designsystem.md       ← output fra fase 1
  brief.md              ← output fra fase 2
  demo/                 ← output fra fase 3 (HTML/CSS/JS)
```

## Sprog
Al kommunikation og dokumentation foregår på dansk.
