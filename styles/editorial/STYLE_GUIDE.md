# Pipe-Works Editorial — Style Guide

**Version:** 1.0.0-draft
**Date:** 2026-02-20
**Status:** Draft — documented from pipe-works-org website CSS
**CSS Source:** `pipe-works-org/site/css/`

---

> **Scope:** This guide covers the **editorial / print-workshop** visual language
> used by the pipe-works.org website — the public-facing pamphleteer voice of the
> Pipe-Works project.
>
> It does **NOT** cover the app-mode tools (Axis Descriptor Lab, Name Generator,
> etc.), which use a completely different dark industrial aesthetic. For tool styles,
> see [`../app/STYLE_GUIDE.md`](../app/STYLE_GUIDE.md).

---

## 1. Design Philosophy

The pipe-works.org website presents itself as a **print workshop broadsheet** —
aged paper pinned to a dark wall, hand-set type, intentionally imperfect alignment.

Core principles:

- **Pamphleteer voice** — the CSS defines a vocabulary; page stylesheets write sentences
- **Print-workshop aesthetic** — aged paper, ink, blood-red accents, pin shadows
- **No build system** — plain CSS, edit and reload
- **Intentional imperfection** — the quirk system adds controlled misalignment
- **Single aesthetic** — no dark/light theme toggle; the look is the identity
- **Zero dependencies** — CSS custom properties, Grid, Flexbox, nothing external

### What This System IS

- A visual identity for the pipe-works.org website
- An aged-broadsheet metaphor carried through every element
- A demonstration of the Pipe-Works world's aesthetic

### What This System IS NOT

- A reusable UI component library
- Applied to any tool, dashboard, or utility interface
- Interchangeable with the app-mode design system

---

## 2. Where the CSS Lives

The editorial CSS lives **exclusively** in the `pipe-works-org` repository. Unlike
the app base CSS, it is not designed to be copied into other projects.

```
pipe-works-org/site/css/
|-- fonts.css                # @font-face declarations
|-- pipe-works-base.css      # Foundation: tokens, reset, shared components
|-- index.css                # Home page (handbill)
|-- goblin-laws.css          # Goblin Laws page (hash-navigation single-law viewer)
|-- three-pillars.css        # Three Pillars page (quirked ASCII art layout)
|-- crooked-pipe.css         # Crooked Pipe interactive fiction game
+-- pipe-works-explore.css   # Explore page (permit form + entity viewer)
```

**Import order on each page:**
`fonts.css` -> `pipe-works-base.css` -> `[page].css`

---

## 3. Colour Palette

The editorial palette is warm, muted, and physically grounded — ink on paper,
blood-red accents, brown fixtures.

### 3.1 Core Palette

| Token | Value | Purpose |
|-------|-------|---------|
| `--paper` | `#f3ecd8` | Aged cream paper — `.sheet` background |
| `--ink` | `#2a1f14` | Primary dark ink — body text |
| `--ink-faded` | `#453728` | Secondary text, margin notes, faded marks |
| `--blood` | `#7a1f1f` | Links, accent borders, highlights |
| `--pin` | `#8b5e3c` | Decorative pin element |
| `--cooling-brown` | `#4a3a2a` | Sheet pin, subtle UI accents |
| `--bg` | `#2b241c` | Dark backdrop behind the paper sheet |

### 3.2 Legacy Newsprint Palette

The base CSS retains a "newsprint" palette from the Daily Undertaking concept.
These tokens exist for potential future use but are not actively applied:

| Token | Value | Note |
|-------|-------|------|
| `--ink-newsprint-black` | `#000` | Absolute black |
| `--ink-newsprint-gray` | `#2b2b2b` | Dark grey |
| `--ink-newsprint-faded` | `#4a4a4a` | Medium grey |
| `--ink-red` | `#c41e3a` | Newsprint red (distinct from `--blood`) |
| `--paper-newsprint` | `#f2efe9` | Cooler white paper |
| `--paper-muted` | `#ebe5d6` | Darker newsprint |
| `--surface-backdrop` | `#2a2a2a` | Neutral dark backdrop |

### 3.3 Comparison with App Palette

| Concept | Editorial | App Tools |
|---------|-----------|-----------|
| Background | `--bg: #2b241c` (warm brown) | `--col-bg: #111214` (cool dark grey) |
| Surface | `--paper: #f3ecd8` (aged cream) | `--col-surface: #1c1e22` (dark panel) |
| Text | `--ink: #2a1f14` (brown-black) | `--col-text: #d4d7dc` (light grey) |
| Accent | `--blood: #7a1f1f` (deep red) | `--col-accent: #f59e0b` (amber) |
| Muted | `--ink-faded: #453728` (warm grey) | `--col-text-muted: #6b7280` (cool grey) |

These are fundamentally different colour temperatures and moods. They should not
be mixed.

---

## 4. Typography

### 4.1 Font Hierarchy

The editorial system uses **six font families**, each with a specific voice:

| Token | Font | Role | Where Used |
|-------|------|------|------------|
| `--font-masthead` | IM Fell English SC | Ceremonial, uppercase | `<h1>` page titles |
| `--font-headline` | Libre Baskerville | Authoritative, clear | `<h2>`, `<h3>` section headings |
| `--font-body` | Crimson Text | Readable, elegant | `<body>` text, `<p>` elements |
| `--font-record` | Courier Prime | Archival, monospace | `.notice`, `.ledger`, `.margin-note`, forms |
| `--font-symbols` | IM Fell English | Decorative, editorial | `.marker`, `.ReferenceMark` |
| `--font-accent` | Special Elite | Typewriter, handwritten | Buttons, accent labels |

### 4.2 Typography Rules

1. **h1** — IM Fell English SC, uppercase, centred, `0.12em` letter-spacing
2. **h2, h3** — Libre Baskerville, bold, `0.02em` letter-spacing, bottom rule
3. **Body** — Crimson Text, `line-height: 1.5`, `0.75rem` vertical margins
4. **Records** — Courier Prime for anything that represents data, ledgers, notices
5. **No type scale tokens** — the website uses direct rem values, not a token system

### 4.3 Comparison with App Typography

| Element | Editorial | App Tools |
|---------|-----------|-----------|
| Headings | Serif (IM Fell English SC, Libre Baskerville) | Monospace (JetBrains Mono stack) |
| Body text | Serif (Crimson Text) | Sans-serif (system-ui) |
| Data/code | Monospace (Courier Prime) | Monospace (JetBrains Mono stack) |
| Buttons | Typewriter (Special Elite) | Monospace (JetBrains Mono) |

---

## 5. Spacing & Layout

### 5.1 Spacing Tokens

| Token | Value | Usage |
|-------|-------|-------|
| `--space-1` | `4px` | Tight gaps |
| `--space-2` | `8px` | Default gaps |
| `--space-3` | `12px` | Section padding |
| `--space-4` | `16px` | Major spacing |
| `--space-5` | `24px` | Large spacing |
| `--space-6` | `32px` | Extra-large spacing |

Note: the editorial system uses `--space-*` (px values), while the app system uses
`--sp-*` (rem values). Different naming, similar scale.

### 5.2 The Sheet

The central layout metaphor: a piece of paper pinned to a dark wall.

```css
.sheet {
  max-width: 42rem;
  margin: 0 auto;
  padding: 3rem 2.5rem 2.5rem;
  background: var(--paper);
  /* Subtle noise texture */
  background-image: radial-gradient(rgba(0,0,0,0.03) 1px, transparent 1px);
  background-size: 3px 3px;
}

/* Fake pin at top centre */
.sheet::before {
  /* 0.75rem brown circle with inset shadow */
}
```

Every page on the website wraps its content in `.sheet`. The dark `--bg` body
background shows around and behind the sheet, creating the "pinned to a wall"
effect.

---

## 6. The Quirk System

The most distinctive feature of the editorial CSS. Quirks add **intentional
misalignment** via CSS transforms — elements look hand-placed rather than
machine-perfect.

### 6.1 How It Works

```css
.u-quirk {
  --quirk-x: 0rem;
  --quirk-y: 0rem;
  --quirk-rotate: 0deg;
  transform:
    translate(
      calc(var(--quirk-x) * var(--quirk-intensity)),
      calc(var(--quirk-y) * var(--quirk-intensity))
    )
    rotate(calc(var(--quirk-rotate) * var(--quirk-intensity)));
}
```

Key design decisions:

- **Transform-based** — quirks don't affect document flow
- **Intensity-scaled** — `--quirk-intensity` multiplies all offsets
- **Responsive** — intensity 1.0 on desktop, 0.3 on mobile, 0 with reduced motion
- **Per-element values** — each element sets its own `--quirk-x`, `--quirk-y`, `--quirk-rotate`

### 6.2 Intensity Levels

| Context | `--quirk-intensity` | Why |
|---------|--------------------|----|
| Desktop (default) | `1` | Full effect |
| Mobile (`<= 600px`) | `0.3` | Readable but still quirky |
| `prefers-reduced-motion` | `0` | Completely disabled |

### 6.3 Example Usage

From `three-pillars.css`:
```css
#ascii-pillar-one {
  --quirk-x: 10rem;
  --quirk-y: -2rem;
  --quirk-rotate: 1.2deg;
}
```

From `index.css`:
```css
#note-austrian-engineering {
  --quirk-x: -3.5rem;
  --quirk-y: 1.4rem;
  --quirk-rotate: -0.8deg;
}
```

Each element defines its own displacement and rotation. The quirk utility class
applies the transform formula. The intensity knob scales everything proportionally.

### 6.4 When NOT to Quirk

- Body text (readability trumps charm)
- Navigation / interactive elements (predictability matters)
- Mobile-primary content at narrow widths
- Anything a screen reader user would interact with

---

## 7. Component Patterns

### 7.1 Sticker

A yellow label, slightly rotated, with a paper-fold glint.

```css
.sticker {
  position: absolute;
  top: 1rem; right: -1.5rem;
  background: #f6e27a;
  color: #2a1f14;
  font-family: 'Arial Black', Impact, sans-serif;
  transform: rotate(6deg);
  /* Paper fold glint via ::after clip-path */
}
```

On mobile, stickers become `position: relative` and reduce rotation.

### 7.2 Rule (Law / Section Block)

Blood-red left border, indented content.

```css
.rule {
  margin-top: 2.5rem;
  padding-left: 1rem;
  border-left: 4px solid var(--blood);
}
```

### 7.3 Margin Note

Small, italic, faded — positioned outside the main text flow on desktop,
inline on mobile.

```css
.margin-note {
  font-family: var(--font-record);
  font-size: 0.75rem;
  font-style: italic;
  color: var(--ink-faded);
  max-width: 18rem;
}
```

### 7.4 ASCII Art

Monospace decorative blocks, typically quirk-positioned.

```css
.ascii code {
  font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, ...;
  font-size: 0.95rem;
  line-height: 1.15;
  color: var(--ink-faded);
}
```

The `.ascii--stamp` variant rotates the content slightly (`-3.8deg`).

### 7.5 Permit Form (Explore Page)

A ledger-style form with repeating horizontal lines and a floating label:

```css
.permit {
  border: 2px solid var(--ink);
  /* Background: tinted paper with repeating ledger lines */
  background:
    color-mix(in srgb, var(--paper) 95%, var(--ink-faded) 5%),
    repeating-linear-gradient(...);
}
```

Inputs are minimal: transparent background, dotted bottom border, record font.
Buttons use Special Elite font with a lifted shadow effect.

### 7.6 Editorial Marks

Decorative symbols using the IM Fell English font:

```css
.marker, .ReferenceMark {
  font-family: var(--font-symbols);
  font-weight: 400;
  color: var(--ink);
}
```

---

## 8. Page-Specific Patterns

Each page extends the base with its own CSS file:

### 8.1 Index (Home)

- Colophon metadata in small monospace
- Actions list with dashed underlines
- Crooked Pipe easter egg (hover-reveal pipe mark)
- Imprint footer with ASCII art

### 8.2 Goblin Laws

- **Hash-based navigation** — no JavaScript required
- `:target` shows the selected law, hides the index
- `main:has(.rule:target) #index { display: none; }`
- Back link appears only when viewing a single law
- Scroll margin for anchor offset

### 8.3 Three Pillars

- Heavily quirked layout — three ASCII art pillars with independent offsets
- Each pillar and margin note has unique quirk values
- Third pillar uses blood-red colour override

### 8.4 Crooked Pipe

- Interactive fiction game
- Door image with aged photo filter: `grayscale(60%) sepia(20%) contrast(95%)`
- Login form with minimal dotted-border styling
- Scene system with progressive reveal animation
- Choice buttons with dotted underlines

### 8.5 Explore

- Permit form with ledger-line background
- Entity profile viewer with ID card grid
- Portrait placeholder with dashed border
- Axis/value rows using definition list grid

---

## 9. Shared Font Files

Both the editorial and app systems use the same self-hosted woff2 files,
declared in separate `fonts.css` / `pipe-works-fonts.css` files.

The font files themselves live in each project's assets directory:

| Project | Font path |
|---------|-----------|
| pipe-works-org | `site/assets/fonts/[Family_Name]/` |
| Name Generator | `webapp/frontend/static/fonts/` |
| (Other tools) | `static/fonts/` (convention) |

The fonts are identical — same OFL-licensed files from Google Fonts. Only the
path prefix differs per project.

---

## 10. Responsive Behaviour

| Breakpoint | Changes |
|------------|---------|
| `<= 460px` | Explore page portrait shrinks, goes single-column |
| `<= 600px` | Quirk intensity 0.3, sheet padding reduced, stickers repositioned |
| `>= 640px` | Multi-column grids activate (explore page) |
| `prefers-reduced-motion` | Quirk intensity 0, all animations disabled |

---

## 11. Accessibility

1. **`prefers-reduced-motion: reduce`** — disables all animations and quirk transforms
2. **`.u-sr-only`** — screen-reader-only utility
3. **`font-display: swap`** — all fonts render immediately with fallback
4. **`scroll-behavior: smooth`** — for hash navigation (goblin laws)
5. **Semantic HTML** — headings, landmarks, lists used structurally
6. **`::selection`** — subtle paper-toned selection highlight

---

## 12. Do's and Don'ts

### Do

- Use the token system (`--paper`, `--ink`, `--blood`) for all colours
- Apply quirks with the `.u-quirk` class and per-element custom properties
- Keep the "pinned broadsheet" metaphor consistent
- Test with `--quirk-intensity: 0` to verify content is readable without quirks
- Use the editorial fonts for their designated roles

### Don't

- Import app-mode tokens (`--col-*`) into the website
- Use amber accent (`#f59e0b`) — that's the app palette, not editorial
- Apply dark/light theme switching — the website has one look
- Use the app component classes (`.btn--primary`, `.card`, `.badge`)
- Add a CSS framework or build system
- Over-quirk — body text and interactive elements should remain straight

---

## 13. Relationship to App System

| Aspect | Editorial (this guide) | App Tools |
|--------|----------------------|-----------|
| **Metaphor** | Broadsheet pinned to a wall | Industrial dashboard |
| **Palette** | Ink + blood on aged paper | Grey + amber on dark surfaces |
| **Typography** | Serif-dominant (6 families) | Monospace-dominant (2 stacks) |
| **Theme** | Single (no toggle) | Dark + light toggle |
| **Layout** | Centred `.sheet`, quirk transforms | Flex/grid panels, fixed shell |
| **Token prefix** | `--ink-*`, `--paper-*` | `--col-*` |
| **CSS location** | `pipe-works-org/site/css/` | Distributable base CSS (this repo) |
| **Reusability** | Website-only | Shared across tool projects |

The app tools system also covers the MUD Server admin shell (which is currently
divergent but being aligned). The two top-level systems share **font files** and
**design values** (craftsmanship, intentionality, no external dependencies) but
are visually and structurally independent.

The app guide lives at [`../app/STYLE_GUIDE.md`](../app/STYLE_GUIDE.md).
