# FlexiWeb Design System

Le design system de **FlexiWeb EVO** : des tokens de marque et un thème
[shadcn/ui](https://ui.shadcn.com/) prêt à poser sur un projet — ou à importer dans
[v0](https://v0.dev/) par URL.

Un seul thème, `flexiweb-theme` : palette verte de marque, **Hanken Grotesk** en corps,
**Fraunces** en display, modes clair et sombre.

## Contenu du dépôt

Tout le contenu servi vit sous `public/`, pensé pour être publié tel quel comme site statique.

| Fichier | Rôle |
|---|---|
| `public/tokens.json` | Les tokens, au format DTCG (`$type` / `$value`) — **source de vérité** |
| `public/theme.css` | Variables CSS shadcn + marque + polices, avec `@theme inline` pour Tailwind v4 — à importer dans un projet |
| `public/registry.json` | Index du registry shadcn (`name: flexiweb`, un item) |
| `public/r/flexiweb-theme.json` | L'item de thème lui-même — **c'est l'URL que consomme v0** |
| `public/index.html` | Page de démonstration du thème |
| `public/_headers` | En-têtes `Content-Type: application/json` et CORS pour `/r/*` et `/registry.json` |

## Utiliser le thème

### Dans un projet

Importer la feuille de style, puis consommer les variables :

```css
@import "./theme.css";
```

```css
background: var(--surface);
color: var(--heading);
font-family: var(--font-serif);
border-radius: var(--radius);
```

`theme.css` définit les variables sous `:root` pour le mode clair et sous `.dark` pour le
mode sombre : la bascule se fait en posant la classe `dark` sur un ancêtre. Le bloc
`@theme inline` les expose à Tailwind v4.

### Dans v0

v0 importe un thème shadcn depuis une **URL publique** pointant sur
`/r/flexiweb-theme.json`.

> **À savoir avant d'essayer : ce dépôt n'est pas hébergé aujourd'hui.** Il n'a ni GitHub
> Pages ni page d'accueil déclarée. Le fichier `public/_headers` utilise la syntaxe de
> Cloudflare Pages / Netlify : `public/` est fait pour être publié chez l'un d'eux, ce qui
> appliquera le bon `Content-Type` et les en-têtes CORS dont v0 a besoin. Cette publication
> reste à faire.
>
> Dépannage : l'URL brute GitHub répond et le JSON y est valide —
> `raw.githubusercontent.com/yg0a1n/flexiweb-registry/main/public/r/flexiweb-theme.json` —
> mais elle est servie en `text/plain` et sans en-tête CORS. C'est précisément ce que
> `_headers` corrige ; je n'ai pas vérifié que v0 s'en contente.

## Ce que contient le thème

**Couleurs de marque** — vert `#16a34a`, primary `#0a5a28`, heading / deep `#0c5526`,
accent `#9acd32`, destructive `#bf000f`.

**Surfaces** — blanc, `surface #f6faf6`, `cream #eef5ee`, `sage #d7edda` / `#e8f3ea`, plus
une famille `sand` chaude.

**Texte** — `#1f2937` (foreground), `#4b5563` (muted), `#6b7280` (faint), border `#e2e8e4`.

**Typographie** — Hanken Grotesk (corps), Fraunces (display, alias `--font-serif`), mono
système. Échelles de taille, graisse, interlignage et interlettrage définies dans les tokens.

**Formes** — radius par défaut `0.625rem`, échelle `sm .375` · `md .625` · `lg .75` ·
`xl 1` · `2xl 1.5rem`. Échelle d'ombres également fournie.

**Modes clair et sombre** — 49 variables chacun, en miroir strict entre `tokens.json`,
`theme.css` et le registry.

## Faire évoluer

Une décision graphique validée par yg0a1n se propage en **un seul commit**, dans les trois
fichiers à la fois : `tokens.json`, `theme.css` et le registry. C'est ce qui garantit que les
trois disent la même chose — un thème importé dans v0 qui diverge du CSS d'un projet est un
design system qui ne fait plus autorité.

Aucune valeur graphique ne vit hors des tokens.

## Historique

**v1.2** (2026-07-19) — neutres chauds, famille `sand`.

**v1.1** (2026-07-04) — `--on-brand` exposé dans `theme.css` (il n'était que dans
`tokens.json`) ; échelle de radius exportée ; slot `--font-display` (Fraunces).
Restés volontairement **locaux aux sites** et donc hors du design system :
`cream-deep`, `yellow` et `border-strong` de site-express, et les `urgent-*` du CMS.

**v1** (2026-07-03) — tokens extraits de `flexiweb-evo.eu`, `b2b.flexiweb-evo.eu` et du
gabarit `p4-garantis.html`, puis arbitrés.

## Licence

Sous licence MIT — voir [`LICENSE`](LICENSE).
