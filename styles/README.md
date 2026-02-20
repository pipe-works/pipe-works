# Pipe-Works Style Guides

This directory contains the design system documentation for the Pipe-Works project.

Pipe-Works uses **two distinct visual languages** that serve different purposes.
They share font files but are otherwise independent systems.

---

## Two Systems

### App Tools (`app/`)

The dark industrial aesthetic used by development tools, dashboards, and utilities.

- **Used by:** Axis Descriptor Lab, Name Generator webapp, MUD Server admin shell, future tool UIs
- **Mood:** Dark surfaces, amber accents, monospace-heavy, data-dense
- **Features:** Dark/light theme toggle, `--col-*` token system, BEM naming for components
- **Files:**
  - `STYLE_GUIDE.md` — Design system documentation
  - `pipe-works-base.css` — Distributable base CSS (tokens, reset, components)
  - `pipe-works-fonts.css` — Self-hosted @font-face declarations
  - `TOKEN_MAP.md` — Variable name mapping between existing projects
  - `MIGRATION_NOTES.md` — How to adopt the base CSS in each project

### Editorial / Website (`editorial/`)

The print-workshop aesthetic used by the pipe-works.org website.

- **Used by:** pipe-works.org (exclusively)
- **Mood:** Aged paper, ink + blood-red accents, serif type, intentional imperfection
- **Features:** Quirk system, single aesthetic (no theme toggle)
- **Files:**
  - `STYLE_GUIDE.md` — Design system documentation
  - *(The actual CSS lives in `pipe-works-org/site/css/`, not here)*

---

## What They Share

- **Font files** — Both systems use the same 6 OFL-licensed font families (Courier Prime,
  Crimson Text, IM Fell English, IM Fell English SC, Libre Baskerville, Special Elite),
  self-hosted as woff2 files
- **Values** — No external dependencies, CSS custom properties throughout,
  accessibility-first, craftsmanship over convenience

## What They Don't Share

| | App Tools | Editorial |
|---|---|---|
| Colour temperature | Cool greys | Warm browns |
| Accent colour | Amber (`#f59e0b`) | Blood red (`#7a1f1f`) |
| Primary font | Monospace | Serif |
| Token prefix | `--col-*` | `--ink-*`, `--paper-*` |
| Theme switching | Yes (dark/light) | No |
| Layout metaphor | Panels + shell | Pinned broadsheet |
| Distributable | Yes (base CSS) | No (website-only) |

---

## For Claude Code

When working on a Pipe-Works project, determine which system applies:

- **Building a tool, dashboard, or API UI?** Follow `app/STYLE_GUIDE.md` and
  use `pipe-works-base.css` as your foundation.
- **Working on pipe-works.org?** Follow `editorial/STYLE_GUIDE.md` and work
  directly in `pipe-works-org/site/css/`.
- **Never mix** the two palettes or token systems in the same interface.
