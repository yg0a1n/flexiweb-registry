# FlexiWeb Design System — v1.1

**v1.1 (2026-07-04)** — gaps remontés par les 4 câblages (valeurs déjà arbitrées, zéro nouveau goût) :
- `--on-brand` exposé dans `theme.css` (était tokens.json only)
- échelle radius exportée : `--radius-sm/.375 · md/.625 · lg/.75 · xl/1 · 2xl/1.5rem` (+ mappings `@theme`)
- slot `--font-display` = Fraunces (alias `--font-serif`) + `font.display` dans tokens.json
- Exclu (décision agent-os #1043) : cream-deep/yellow/border-strong (site-express) et urgent-* (cms) restent **site-local** — le DS reste canonique.

Bootstrap du DS FlexiWeb (volet V2b). Source : extraction `flexiweb-evo.eu` + `b2b.flexiweb-evo.eu` + gabarit `p4-garantis.html`. Décisions **arbitrées par yg0a1n le 2026-07-03**.

## Contenu
| Fichier | Rôle |
|---------|------|
| `tokens.json` | tokens design (DTCG-like) — **source de vérité** |
| `theme.css` | variables CSS shadcn + marque + fonts (+ `@theme` Tailwind v4) — à `@import` dans un projet |
| `registry.json` + `r/flexiweb-theme.json` | **registry shadcn** → importable dans **v0** |
| `gabarits/showcase.html` | démo visuelle + gabarit réutilisable |
| `SHORTLIST-tokens-v1.md` | l'inventaire extrait + les décisions |

## Décisions arbitrées (v1)
- **Vert marque** `#16a34a` · **primary** `#0a5a28` · **heading/deep** `#0c5526` · **accent** `#9acd32`
- **Surfaces** : blanc `#fff`, surface `#f6faf6`, cream `#eef5ee`, **sage** `#d7edda` / `#e8f3ea`
- **Texte** : `#1f2937` (foreground), `#4b5563` (muted), `#6b7280` (faint) · **border** `#e2e8e4`
- **Destructive** `#bf000f`
- **Typo** : **Hanken Grotesk** (corps) + **Fraunces** (display serif) + mono défaut ; échelle 12→60 ; weights 400/500/600/700
- **Radius** défaut `0.625rem` (échelle .375 / .625 / .75 / 1 / 1.5)
- **Dark mode** : reporté en v2

## Utiliser
### Dans un projet (moi / SiteExpress)
```css
@import "./theme.css";
```
Puis utiliser les variables : `background: var(--surface)`, `color: var(--heading)`, `font-family: var(--font-serif)`, `border-radius: var(--radius)`…

### Dans v0
Héberger ce dossier en repo public GitHub → v0 importe le thème via l'endpoint `/r/flexiweb-theme.json` (registry shadcn). Le thème applique les tokens ci-dessus aux composants shadcn.

## Faire évoluer
Toute nouvelle décision graphique **validée par yg0a1n** entre dans `tokens.json` + `theme.css` + le registry = **un commit**. Jamais de valeur graphique hors-token (cf. rule `02-design-system-flexiweb`).
