---
version: alpha
name: nuit-atelier
description: Thème FlexiWeb de nuit. Sections de nuit alternées avec le sable, halo citron, titres d'affiche en Instrument Serif. Prolonge flexiweb-theme (aucune valeur redéfinie). Extrait de /atelier en production (https://www.flexiweb-evo.eu/atelier).
omitted: []
colors:
  nuit: "#06200f"
  nuit-texte: "#f6faf6"
  nuit-attenue: "#b5c7bb"
  partiel-encre: "#7c4a03"
  brand-accent: "#9acd32"
  sand: "#f6eedf"
  sand-deep: "#e8d8bc"
  heading: "#0c5526"
typography:
  affiche:
    fontFamily: Instrument Serif
    fontWeight: 400
  display:
    fontFamily: Fraunces
    fontWeight: 600
  body:
    fontFamily: Hanken Grotesk
    fontWeight: 400
rounded:
  card: 22px
---

# DESIGN.md — nuit-atelier

Origine : direction « nuit d'atelier » (26/11/2026), en production sur https://www.flexiweb-evo.eu/atelier.

## Overview

La première passe sur /atelier ne changeait que des filets et des grilles ; yg0a1n n'y a vu « aucun changement ». Ce thème change ce qui se voit en premier : **le fond** (sections de nuit vert très sombre, alternées avec le sable), **la police d'affichage** (Instrument Serif, en grand et en italique), **le halo citron** du bandeau et de l'appel à l'action, et **des cartes qui réagissent au survol**. Il s'adresse à une page vitrine ou éditoriale de la marque FlexiWeb, qui doit marquer au premier coup d'œil.

## Colors

Toutes les couleurs de marque viennent de flexiweb-theme. Le thème n'ajoute que la nuit (`nuit`, `nuit-texte`, `nuit-attenue`, `nuit-filet`), l'encre d'une pastille « en partie » sur sable foncé, et les deux halos (brand-accent à 30 %).

Contrastes (Contrast Checker WebAIM, mesurés le 26/11 pour le brief v2) :

| Paire | Ratio | Usage |
|---|---|---|
| nuit-texte `#f6faf6` sur nuit `#06200f` | 16,3 | titres et texte sur la nuit |
| brand-accent `#9acd32` sur nuit | 9,13 | chiffre mis en avant sur la nuit (tout texte permis) |
| nuit-attenue `#b5c7bb` sur nuit | 9,70 | texte secondaire sur la nuit |
| nuit sur brand-accent | 9,13 | si un aplat citron porte du texte |
| brand-deep `#0c5526` sur sand `#f6eedf` | 7,77 | titres sur le sable |
| muted-foreground `#4b5563` sur sand | 6,55 | texte secondaire sur le sable |
| partiel-encre `#7c4a03` sur sand-deep `#e8d8bc` | 5,27 | pastille « en partie » |
| brand `#16a34a` sur blanc | 3,29 | barre d'accent et icônes seulement, jamais un libellé |

## Typography

Instrument Serif (OFL) pour h1, h2 et les grands chiffres : 400, l'italique pour le titre du bandeau. Fraunces (flexiweb-theme) reste la police des h3 et le repli de l'affiche ; Hanken Grotesk, le texte. Tailles : h1 `clamp(64px, 10vw, 128px)`, h2 `clamp(40px, 5vw, 64px)`, chiffre clé 88 px, chiffre de tuile 64 px (72 et 52 sous 560 px).

## Layout

Bandeau pleine largeur, centré. Sections alternées : nuit, sable, blanc, jamais deux nuits de suite. Chiffres clés en colonnes séparées par des filets (4 en bureau, 2 sous 900 px, 1 sous 560 px). Grille de cartes en 3, 2 puis 1 colonne.

## Elevation & Depth

Les cartes blanches portent une ombre teintée de vert (`ombre-carte`) ; sur la nuit, une carte blanche garde ses contrastes du clair.

## Shapes

Cartes à 22 px. Les autres rayons sont ceux de flexiweb-theme.

## Motion & Micro-interaction

Un seul geste : la grille à filets. Au survol (appareils qui survolent) et au focus, la barre de 4 px grandit de 24 à 40 px et passe au vert de marque, le titre glisse de 8 px, en 200 ms. Avec `prefers-reduced-motion`, seule la couleur change. Aucun chiffre qui défile, aucun effet au défilement.

## Voice & Content Strategy

Le thème ne porte aucun texte. Le contenu reste celui du projet ; sur /atelier, il est figé (données réelles).

## Components

| Élément | Composant | Site | Lien |
|---|---|---|---|
| Bandeau (`.na-bandeau`) | Veil Hero Section 1 (Tailark, MIT) | Tailark | https://github.com/tailark/blocks/blob/main/registry/bases/radix/veil/blocks/hero-section/one/hero-section.tsx |
| Chiffres clés (`.na-chiffres`) | Stats 1 (Tailark, MIT) | Tailark | https://github.com/tailark/blocks/blob/main/registry/bases/radix/mist/blocks/stats/one.tsx |
| Tuiles sur la nuit | Stats 2 (Tailark, MIT) | Tailark | https://github.com/tailark/blocks/blob/main/registry/bases/radix/mist/blocks/stats/two.tsx |
| Grille à filets avec survol (`.na-grille`) | Feature Section with hover effects (Manu Arora, MIT) | 21st.dev | https://21st.dev/@manuarora700/components/feature-section-with-hover-effects |
| Icônes | Lucide | Lucide | https://lucide.dev/icons/ |
| Police d'affichage | Instrument Serif (OFL) | Google Fonts | https://fonts.google.com/specimen/Instrument+Serif |
| Palette de nuit (5 rôles) | texte f6faf6, fond 06200f, primaire 9acd32, secondaire 0c5526, accent 16a34a | Realtime Colors | https://realtimecolors.com/?colors=f6faf6-06200f-9acd32-0c5526-16a34a |
| Contrôle | tableau ci-dessus | Contrast Checker (WebAIM) | https://webaim.org/resources/contrastchecker/ |

Implémentation de référence : `flexiweb-landing-page/src/app/[locale]/(public)/atelier/atelier.css` (bb39755), où les mêmes règles sont portées par `.atelier`.

## Do's and Don'ts

- À faire : alterner nuit et clair ; un seul chiffre en citron par rangée ; le focus bicolore (contour blanc + anneau brand-deep), visible sur la nuit comme sur le clair ; charger Instrument Serif pour la seule page qui l'utilise.
- À ne pas faire : le vert de marque `#16a34a` en texte (3,29) ; une pastille posée sur `sand` quand la section est elle-même sable (elle disparaît : la poser sur `sand-deep`) ; des effets de défilement, du néon, des chiffres qui montent (écartés dès l'origine) ; deux sections de nuit de suite.
