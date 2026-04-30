# PocketSeed Design System

The visual language behind PocketSeed v1, extracted from the sales deck and packaged so any future project — decks, web apps, marketing pages, internal tools — can pick it up in one line.

**Direction in one paragraph.** Modern, friendly, light, inviting. Not loud — PocketSeed lives inside other brands and needs to fit beside them without changes. Think of it as a **nutrition label on a package**: a recognisable visual language for proof and data that never fights with whatever it sits on. Content does the work; the system is the frame. See [`DESIGN.md`](DESIGN.md) for the full direction and rules.

> **AI agents:** read [`DESIGN.md`](DESIGN.md) before writing code that uses this system.

## TL;DR — pull it into any project

The system is **plain CSS + assets**. No build, no dependencies, no install. Pick a flavor:

### One-line CDN (recommended)

The repo is public, so [jsDelivr](https://www.jsdelivr.com/) serves it as a CDN with no setup. Pin to a version tag for stability:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/AGKDesigns/PSSlide_Designsystem@v1/css/pocketseed.css">
```

…or follow `main` for the latest (will move under you):

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/AGKDesigns/PSSlide_Designsystem@main/css/pocketseed.css">
```

### Copy into your project

Clone or download, then drop `css/` and `assets/` wherever your static files live:

```html
<link rel="stylesheet" href="/static/pocketseed/css/pocketseed.css">
```

### Bundler (React / Vue / Svelte / Next)

Copy the files into the project (or git-submodule the repo) and import once at the entry point:

```ts
import 'pocketseed-design-system/css/pocketseed.css';
```

---

Then just use the classes. Everything is namespaced `.ps-` so it never collides with whatever else is on the page:

```html
<section class="ps-bg-paper">
  <span class="ps-eyebrow">Three features, one story</span>
  <h2 class="ps-h-title">
    Replace the PDF report with a
    <span class="ps-serif">living credential.</span>
  </h2>
  <ul class="ps-bullets">
    <li>Tamper-proof and signed</li>
    <li>Evidence travels with the claim</li>
  </ul>
</section>
```

## Browse the system

The full set of specimens is hosted at **<https://pocketseed-design-system.pages.dev>** *(deploys on every push to `main` via Cloudflare Pages)*. Use it as the reference site when designing — colors, type, components, slide templates, login screens, the lot. AI agents can also fetch the spec pages directly from there.

## What's in the box

```
PSSlide_Designsystem/
├── README.md                   ← this file · adoption + reference
├── DESIGN.md                   ← agent guide · direction, rules, recipes
├── direction.html              ← full design-direction document (web)
├── index.html                  ← landing page · entry to the spec site
├── _headers                    ← Cloudflare Pages cache + security headers
├── css/
│   ├── pocketseed.css          ← all-in-one entry (use this)
│   ├── tokens.css              ← design tokens (CSS variables)
│   ├── base.css                ← resets and element defaults
│   ├── type.css                ← type ramps (slide + web)
│   ├── components.css          ← deck/marketing UI patterns
│   └── webapp.css              ← forms, menus, alerts, modals, avatars, tabs
├── assets/
│   ├── pocketseed-logo.png         ← full lockup · use on light surfaces
│   ├── pocketseed-logo-white.png   ← light lockup · use on dark surfaces
│   └── pocketseed-mark.png         ← icon-only mark · favicons, hero accents
└── specimens/
    ├── colors.html             ← palette + accent presets
    ├── typography.html         ← type ramp · slide & web scale
    ├── components.html         ← every component, in isolation
    ├── patterns.html           ← composed slide archetypes
    ├── slide-template.html     ← copy-paste starting point for new decks
    ├── web-page.html           ← same language applied to a web page
    ├── forms.html              ← inputs, dropdowns, alerts, modal, tabs
    └── login.html              ← sign-in / auth screen pattern
```

Open `index.html` in a browser to navigate the specimens visually.

## Tokens (the source of truth)

All design decisions are CSS custom properties in `css/tokens.css`. If you only remember one thing, remember this — change the token, the whole system updates.

### Color

| Token | Hex | Use |
|---|---|---|
| `--ps-paper` | `#f7f4ec` | Default page background (warm cream) |
| `--ps-paper-warm` | `#efeadd` | Slightly warmer alt surface |
| `--ps-card` | `#ffffff` | Cards on paper |
| `--ps-ink` | `#1a2535` | Default text & dark surfaces |
| `--ps-ink-soft` | `#2d3a4d` | Body text |
| `--ps-muted` | `#6b7280` | Captions, meta |
| `--ps-line` / `--ps-line-soft` | `#e5e0d3` / `#efeae0` | Borders |
| `--ps-teal` | `#2dadc7` | Brand teal — accent on **dark** surfaces |
| `--ps-blue` | `#3b6cf0` | Brand blue |
| `--ps-purple` | `#6a4ed8` | Used in orb gradient |
| `--ps-green` / `--ps-green-deep` | `#4caf50` / `#2f7a3a` | Brand green — `green-deep` is the accent on **light** surfaces |

### Accent rule

`--ps-accent` switches automatically with the surface:

- **Light surfaces** (`.ps-bg-paper`, `.ps-bg-warm`, `.ps-bg-card`, default body) → forest green (`--ps-green-deep`)
- **Dark surfaces** (`.ps-bg-ink`) → teal (`--ps-teal`)

This is the look from the sales deck: cream pages talk in green, ink pages talk in teal. Override per-component with `.ps-accent-teal`, `.ps-accent-blue`, `.ps-accent-purple`, `.ps-accent-leaf`, `.ps-accent-ink`.

### Typography

- **Inter** — body & UI · 400/500/600/700/800
- **Instrument Serif** — italic editorial accents inside headlines
- **JetBrains Mono** — micro-type, IDs, timestamps, tabular figures

Two ramps:

- `.ps-h-mega` / `.ps-h-display` / `.ps-h-title` / `.ps-h-section` / `.ps-h-subtitle` / `.ps-lead` / `.ps-body-lg` / `.ps-body` / `.ps-small` — built for the **1920×1080 slide stage**
- `.ps-web-display` / `.ps-web-title` / `.ps-web-section` / `.ps-web-subtitle` / `.ps-web-lead` / `.ps-web-body` / `.ps-web-small` — built for **everyday screens**

Plus `.ps-eyebrow` (kicker), `.ps-serif` (italic accent), `.ps-mono` (mono micro-type).

### Spacing & radii

Spacing tokens follow a denominated scale: `--ps-space-2` through `--ps-space-100`. Slide-stage padding is `--ps-stage-pad-x` (100px) and `--ps-stage-pad-top` (100px). Radii: `sm` (6) → `md` (10) → `lg` (14) → `xl` (18) → `2xl` (20) → `3xl` (24) → `pill` (999).

## Components (the everyday vocabulary)

| Class | What it is |
|---|---|
| `.ps-bg-paper` / `.ps-bg-warm` / `.ps-bg-card` / `.ps-bg-ink` | Surface backgrounds. `ps-bg-ink` flips text colors automatically. |
| `.ps-card` (+ `.ps-card-bare` / `.ps-card-tight` / `.ps-card-ink`) | The workhorse surface container · `.ps-card-ink` is a stand-alone dark variant |
| `.ps-feature-card` | Three-up grid pattern from the deck (numerator + accent pill + headline) |
| `.ps-pill` (+ `-solid` / `-accent` / `-sm` / `-xs`) | Tag / badge / status |
| `.ps-bullets` | Quiet bullet list with a short accent dash |
| `.ps-list-item` + `.ps-list-icon` + `.ps-list-title` + `.ps-list-sub` | Icon + title + sub card (chain-of-authority / list-of-five pattern) · glassy on ink surfaces |
| `.ps-rule` | 1px line · matches the surface |
| `.ps-numarker` | Mono index marker |
| `.ps-mark` | Icon-only brand mark image (set `--ps-mark-size` to scale) |
| `.ps-brandmark` | Full logo lockup with optional inline text |
| `.ps-browser` + `.ps-browser-bar` + `.ps-url` | Mockup container for product / credential pages |
| `.ps-chrome` | Slide header band: logo left, meta right |
| `.ps-slide` | Full-bleed slide frame |
| `.ps-stage` / `.ps-stage-fit` | 1920×1080 stage · scale to fit any container |
| `.ps-grain` / `.ps-glow` | Decorative dotted grid + brand glow |
| `.ps-quote` | Pull-quote on dark with serif italic body |
| `.ps-btn` | App-scale button (default · compact, rounded). Modifiers: `-primary`, `-accent`, `-ghost`, `-danger`, `-sm`, `-icon`. Add `-cta` for marketing pill-scale, `-lg` for hero. |
| `.ps-ask-bar` | "Ask a question…" input mock |
| `.ps-stat` + `.ps-stat-label` + `.ps-stat-value` | Tabular figures |

Layout helpers (no Tailwind — these are direct, opinionated): `.ps-grid-2/3/4/5`, `.ps-flex`, `.ps-flex-col`, `.ps-items-center`, `.ps-justify-between`, `.ps-gap-{8,12,16,20,24,32,40,48,56,64}`.

See `specimens/components.html` for every one in isolation.

## Web app components (`webapp.css`)

For product UI built on top of the system. All web-scale by default; pair with `.ps-btn` for actions.

| Class | What it is |
|---|---|
| `.ps-field` + `.ps-label` + `.ps-helper` (+ `.ps-error`) | Vertical field stack |
| `.ps-input` / `.ps-textarea` / `.ps-select` | Form controls · `aria-invalid="true"` for error styling |
| `.ps-input-group` + `.ps-input-prefix` / `.ps-input-suffix` | Inputs with leading/trailing addons |
| `.ps-checkbox` / `.ps-radio` + `.ps-check-row` | Native check & radio with custom layout (uses `accent-color`) |
| `.ps-switch` + `.ps-switch-track` | Toggle |
| `details.ps-dropdown` + `.ps-menu` + `.ps-menu-item` (+ `.ps-menu-label` / `.ps-menu-divider` / `.ps-menu-danger`) | No-JS popover dropdown |
| `.ps-alert` (+ `-info` / `-success` / `-warn` / `-error`) | Banner alerts |
| `.ps-modal-overlay` + `.ps-modal-card` + `.ps-modal-header/body/footer` | Dialog |
| `.ps-avatar` (+ `.ps-avatar-stack`) | Circular avatars · use `--ps-avatar-size` to scale |
| `.ps-tabs` + `.ps-tab` (with `aria-selected="true"` for active) | Tab bar |
| `.ps-table` | Basic data table |
| `.ps-auth-shell` + `.ps-auth-card` | Centered auth-screen scaffold |
| `.ps-divider` | Horizontal rule with optional centered label |

See `specimens/forms.html` for everything in isolation, and `specimens/login.html` for an end-to-end auth pattern.

## Building a new thing on the system

- **A new sales deck** — open `specimens/slide-template.html` and copy a `<div class="ps-slide …">` block. Each slide is a 1920×1080 frame; build as many as you need.
- **A marketing or product page** — open `specimens/web-page.html` for a full reference page (hero, three-up features, stats band, pitch on ink, footer). Copy whatever fits.
- **A web app** — open `specimens/forms.html` for the form/menu/alert/modal/avatar/tabs vocabulary, and `specimens/login.html` for an end-to-end auth pattern.

If a project already has its own design tokens, import only `tokens.css` and rebuild on top. **The tokens are the contract; components are conveniences.**

## Conventions that matter

1. **One accent at a time.** Don't mix teal, blue, and green in the same headline — the system has variants for a reason.
2. **Earn the serif italic.** Use it on one word per headline, max. It's flavor, not a default.
3. **Quiet by default.** Pages should breathe. Big type, big padding, restrained color. The deck is built around `100px` slide padding for a reason.
4. **Mono is for micro.** IDs, codes, timestamps, URLs, eyebrow markers. Not paragraphs.
5. **Respect the surface.** Light and dark surfaces flip the accent automatically — don't hardcode a color when the system would have switched it for you.

## Versioning & releases

The system follows lightweight semver via git tags. Projects pin via the jsDelivr URL: `@v1` (latest 1.x), `@v1.0.0` (exact), or `@main` (untagged latest, will move).

Cutting a release:

```bash
git tag v1.0.0       # or whatever the next version is
git push --tags      # jsDelivr sees it within minutes
```

Future iterations should:

- Add new tokens / components rather than mutate existing ones
- Bump the patch / minor / major version per the change
- Document any breaking change at the top of this README

## Deploying the spec site

The repo is published to Cloudflare Pages on every push to `main`. To trigger a one-off deploy from a local checkout:

```bash
wrangler pages deploy . --project-name=pocketseed-design-system
```

Cloudflare Pages picks up the static files directly — no build step. The `_headers` file at the root sets sensible cache + security headers; HTML caches short, CSS/assets cache longer.

## Credits

Visual language: PocketSeed brand · v1 sales deck (Apr 2026).
Extracted: 30 Apr 2026.
