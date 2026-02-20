# Pipe-Works App Tools — Style Guide

**Version:** 1.0.0-draft
**Date:** 2026-02-20
**Status:** Draft — extracted from Axis Descriptor Lab (canonical) + Name Generator (derivative)

---

> **Scope:** This guide covers the **app-mode** visual language used by Pipe-Works
> development tools, dashboards, and utilities:
>
> - **Axis Descriptor Lab** — canonical source of this design system
> - **Name Generator webapp** — derivative, needs token rename migration
> - **MUD Server admin shell** — divergent, needs full aesthetic alignment
> - **Future tool UIs** — should adopt this system from the start
>
> It does **NOT** cover:
> - The **pipe-works.org website**, which uses a completely different editorial /
>   print-workshop aesthetic — see [`../editorial/STYLE_GUIDE.md`](../editorial/STYLE_GUIDE.md)
> - The **MUD Server play UI**, which has its own design considerations

---

## 1. Design Philosophy

The Pipe-Works app aesthetic is defined by:

- **Dark industrial baseline** — deep greys, amber accents, monospace type
- **Warm paper light theme** — aged parchment tones, darker amber for contrast
- **No external CSS dependencies** — plain CSS custom properties, Grid, Flexbox
- **Accessibility-first** — focus rings, ARIA-live regions, colour contrast >= 4.5:1
- **Data-dense, compact layouts** — monospace-heavy, functional over decorative

### What This System IS

- A shared foundation for tool and dashboard interfaces
- Designed for interacting with data, APIs, and build pipelines
- Dark/light theme support via `data-theme` attribute

### What This System IS NOT

- The pipe-works.org website aesthetic (that's the editorial system)
- A general-purpose CSS framework
- Opinionated about layout beyond basic shell patterns

---

## 2. Colour System

### 2.1 Variable Naming Convention

**Canonical prefix: `--col-`** (from Axis Descriptor Lab)

The name generator currently uses unprefixed names (`--bg`, `--text`, `--accent`).
New projects MUST use the `--col-` prefix for clarity and to avoid collisions with
CSS properties.

| Category | Token | Dark Value | Light Value | Purpose |
|----------|-------|------------|-------------|---------|
| **Background** | `--col-bg` | `#111214` | `#f4f1ec` | Page background |
| **Surface** | `--col-surface` | `#1c1e22` | `#faf8f5` | Panel/card background |
| **Surface 2** | `--col-surface-2` | `#24272d` | `#efece6` | Elevated surface (inputs, nested panels) |
| **Border** | `--col-border` | `#2e3138` | `#d6d0c6` | Subtle dividers |
| **Border Hi** | `--col-border-hi` | `#444952` | `#b8b0a4` | Focused/highlighted borders |
| **Text** | `--col-text` | `#d4d7dc` | `#2c2a26` | Primary text |
| **Text Muted** | `--col-text-muted` | `#6b7280` | `#7a7568` | Secondary/label text |
| **Text Dim** | `--col-text-dim` | `#3d4149` | `#c4bfb5` | Placeholders, very faint |
| **Accent** | `--col-accent` | `#f59e0b` | `#c27b0a` | Primary amber accent |
| **Accent Dim** | `--col-accent-dim` | `#b45309` | `#a06508` | Pressed/hover states |
| **Accent Glow** | `--col-accent-glow` | `rgba(245,158,11,0.15)` | `rgba(194,123,10,0.12)` | Subtle highlight background |
| **OK** | `--col-ok` | `#22c55e` | `#16a34a` | Success/valid |
| **Error** | `--col-err` | `#ef4444` | `#dc2626` | Error states |
| **Warning** | `--col-warn` | `#fb923c` | `#ea580c` | Warning states |
| **Info** | `--col-info` | `#60a5fa` | `#2563eb` | Informational |

### 2.2 Diff Colours

| Token | Dark Value | Light Value |
|-------|------------|-------------|
| `--col-diff-add` | `rgba(34,197,94,0.18)` | `rgba(22,163,74,0.14)` |
| `--col-diff-del` | `rgba(239,68,68,0.18)` | `rgba(220,38,38,0.14)` |
| `--col-diff-add-text` | `#86efac` | `#166534` |
| `--col-diff-del-text` | `#fca5a5` | `#991b1b` |

### 2.3 Code/Editor Colours

| Token | Dark Value | Light Value |
|-------|------------|-------------|
| `--col-code-bg` | `#0d0f12` | `#ffffff` |
| `--col-code-text` | `#d4d7dc` | `#2c2a26` |
| `--col-code-inline` | `#f59e0b` | `#c27b0a` |

### 2.4 Theme Switching

**Mechanism:** `data-theme` attribute on `<html>`

```html
<!-- Dark (default — no attribute needed) -->
<html>

<!-- Light -->
<html data-theme="light">
```

Dark theme is the default. Light theme overrides all `--col-*` tokens via the
`[data-theme="light"]` selector in `pipe-works-base.css`.

---

## 3. Typography

### 3.1 Font Systems

The app tools use two font systems:

#### Primary: App-Mode Fonts

| Token | Stack | Usage |
|-------|-------|-------|
| `--font-mono` | `"JetBrains Mono", "Fira Code", "Cascadia Code", "Consolas", monospace` | Headings, buttons, inputs, code, tables, labels — ALL structural/interactive elements |
| `--font-ui` | `system-ui, -apple-system, "Segoe UI", sans-serif` | Body text, output prose, descriptions |

**Rule:** `--font-mono` is dominant in app mode. It covers every interactive and
structural element. `--font-ui` is only for body text and prose output.

#### Secondary: Editorial Fonts (Available But Not Default)

The base CSS also defines the editorial font tokens for use in branded sections
(about pages, help panels, splash screens):

| Token | Font | Usage |
|-------|------|-------|
| `--font-masthead` | `"IM Fell English SC"` | Page titles, mastheads |
| `--font-headline` | `"Libre Baskerville"` | Section headings |
| `--font-body` | `"Crimson Text"` | Body text |
| `--font-record` | `"Courier Prime"` | Ledger entries, data |
| `--font-symbols` | `"IM Fell English"` | Editorial marks |
| `--font-accent` | `"Special Elite"` | Typewriter accent |

These are **not** applied by default in app mode. Use them explicitly when you want
the pipe-works editorial voice in a specific section.

### 3.2 Self-Hosted Font Files

All fonts are declared in `pipe-works-fonts.css` (separate file for caching).
See that file for the full @font-face inventory.

| Font | Weights | Styles | Licence |
|------|---------|--------|---------|
| Courier Prime | 400, 700 | normal, italic, bold-italic | OFL |
| Crimson Text | 400, 600, 700 | normal, italic | OFL |
| IM Fell English | 400 | normal, italic | OFL |
| IM Fell English SC | 400 | normal | OFL |
| Libre Baskerville | 400–700 (variable) | normal, italic | OFL |
| Special Elite | 400 | normal | OFL |

### 3.3 Type Scale

| Token | Size | Usage |
|-------|------|-------|
| `--text-xs` | `0.70rem` | Labels, badges, meta text |
| `--text-sm` | `0.80rem` | Secondary text, table content |
| `--text-base` | `0.875rem` | Body text (14px at default) |
| `--text-lg` | `1.0rem` | Headings, titles |
| `--text-xl` | `1.15rem` | Large headings |

### 3.4 Typography Rules

1. **Headings** (h1–h6), **buttons**, **tabs**, **inputs**, **selects**, **textareas**,
   **tables**, **code**: Use `--font-mono`
2. **Body text**, **output prose**: Use `--font-ui`
3. **Letter spacing:** `0.02em` for headings/titles, `0.06–0.08em` for uppercase labels
4. **Text transform:** `uppercase` for section labels, panel headings, table headers
5. **Antialiasing:** `-webkit-font-smoothing: antialiased` on body

---

## 4. Spacing System

### 4.1 Spacing Tokens

| Token | Value | Usage |
|-------|-------|-------|
| `--sp-1` | `0.25rem` (4px) | Tight gaps, badge padding |
| `--sp-2` | `0.5rem` (8px) | Default gap, input padding |
| `--sp-3` | `0.75rem` (12px) | Panel padding, section gaps |
| `--sp-4` | `1rem` (16px) | Major gaps, header padding |
| `--sp-6` | `1.5rem` (24px) | Large spacing, header padding |

### 4.2 Layout Dimensions

| Token | Value | Usage |
|-------|-------|-------|
| `--header-h` | `2.75rem` | App header height |
| `--statusbar-h` | `1.75rem` | Status bar height |
| `--panel-pad` | `1rem` | Default panel padding |

### 4.3 Border Radii

| Token | Value | Usage |
|-------|-------|-------|
| `--radius-sm` | `4px` | Inputs, buttons, badges |
| `--radius-md` | `8px` | Cards, preview sections |
| `--radius-lg` | `12px` | Modals, large cards |

---

## 5. Component Patterns

### 5.1 App Shell

```
+-----------------------------------------------------+
|  .app-header  (flex, z-100)                          |
|  |-- .app-header__title (mono, accent, 700)          |
|  |-- .tabs (optional)                                |
|  +-- .theme-toggle (push right)                      |
+-----------------------------------------------------+
|  .app-main (flex: 1, overflow-y: auto)               |
|  |-- .panel--dark (darker bg)                        |
|  |-- .panel (standard surface)                       |
|  +-- .panel--elevated (surface-2)                    |
+-----------------------------------------------------+
|  .status-bar (flex, z-100)                           |
|  +-- .status-bar__text (mono, xs, muted)             |
+-----------------------------------------------------+
```

### 5.2 Buttons

| Class | Background | Border | Text | Usage |
|-------|-----------|--------|------|-------|
| `.btn--primary` | `--col-accent` | transparent | `--col-button-text` | Primary actions |
| `.btn--secondary` | transparent | `--col-border-hi` | `--col-text` | Secondary actions |
| `.btn--ghost` | transparent | none | `--col-text-muted` | Tertiary/icon actions |
| `.btn--icon` | transparent | `--col-border` | `--col-text` | Icon-only (32x32) |

**States:**
- `:hover:not(:disabled)` — primary darkens, secondary gains accent border+colour
- `:disabled` — `opacity: 0.4`, `cursor: not-allowed`
- `.is-active` (secondary) — amber border + glow background

**Sizes:**
- Default: `--text-sm`, `--sp-1` / `--sp-3` padding
- `.btn--sm`: `--text-xs`, `2px` / `--sp-2` padding
- `.btn--full`: `width: 100%`

### 5.3 Inputs

| Element | Background | Border | Font |
|---------|-----------|--------|------|
| `.input` | `--col-surface-2` | `--col-border` | `--font-mono`, `--text-sm` |
| `.select` | Same + custom caret | Same | Same |
| `.code-editor` | `--col-code-bg` | `--col-border` | `--font-mono`, `--text-xs` |
| `.range-input` | Track: `--col-border`, Thumb: `--col-accent` | none | N/A |
| `input[type="checkbox"]` | native | N/A | `accent-color: --col-accent` |

**Focus state:** `border-color: --col-accent`, no outline (inputs manage their own)

### 5.4 Cards

```css
.card             /* border + radius-lg + surface-2 bg */
.card--compact    /* radius-md, tighter padding */
.card--outlined   /* lighter bg using color-mix */
.card__heading    /* uppercase, muted, 0.95rem */
```

### 5.5 Tables

- **Headers:** uppercase, `--text-xs`, `0.06em` letter-spacing, muted colour
- **Cells:** `--sp-1` / `--sp-2` padding, half-opacity border-bottom
- **Numeric columns:** `.col-numeric` for right-aligned tabular-nums

### 5.6 Badges

| Variant | Background | Text |
|---------|-----------|------|
| Default (success) | `--col-ok` | `#111` |
| `.badge--err` | `--col-err` | `#fff` |
| `.badge--warn` | `--col-warn` | `#111` |
| `.badge--info` | `--col-info` | `#fff` |
| `.badge--muted` | `--col-surface-2` | `--col-text-muted` |
| `.badge--active` | `--col-accent` | `#111` |

### 5.7 Modals

```css
.modal            /* fixed inset, grid place-items center, z-50 */
.modal.hidden     /* display: none */
.modal__backdrop  /* absolute inset, --col-backdrop */
.modal__card      /* surface bg, radius-lg, min(640px, 90vw) */
.modal__header    /* flex, space-between */
.modal__actions   /* flex, justify-end */
```

### 5.8 Scrollbars

Thin 6px WebKit scrollbars, transparent track, `--col-border-hi` thumb,
accent on hover. Firefox gets `scrollbar-width: thin`.

### 5.9 Spinner

12px amber-top border circle, `0.7s` linear spin animation.

---

## 6. Animation

| Token | Value | Usage |
|-------|-------|-------|
| `--transition-fast` | `100ms ease` | Hover, border changes |
| `--transition-med` | `200ms ease` | Panel transitions |

Animations respect `prefers-reduced-motion: reduce`.

---

## 7. Responsive Breakpoints

| Breakpoint | Layout Changes |
|------------|----------------|
| `<= 980px` | Multi-column grids collapse |
| `<= 800px` | Form grids go single-column |
| `<= 640px` | Header wraps, all grids single-column |

---

## 8. CSS Architecture

### 8.1 File Structure

```
static/
|-- fonts/                   # Self-hosted woff2 files
|-- pipe-works-fonts.css     # @font-face declarations
|-- pipe-works-base.css      # Tokens + reset + components
+-- app.css                  # App-specific styles
```

Import order: `fonts.css` -> `base.css` -> `app.css`

### 8.2 CSS Naming Conventions — BEM + Flat Layout

This project uses **BEM (Block__Element--Modifier) for components** and
**flat descriptive names for layout wiring**. State is always `.is-*`.

#### What is a Component? What is Layout?

- **Component** = has children (elements) and/or visual states. Could
  conceivably be moved to a different page and still make sense.
  Examples: a card, a button group, a table with headers, a modal.

- **Layout** = arranges components on a specific page. Describes spatial
  relationships (grids, splits, positioning). Tied to a particular view.
  Examples: a two-column split, a sidebar grid, a dashboard arrangement.

#### BEM Rules (Components)

```css
/* Block — the component root */
.generation-card { ... }

/* Element — a child that only makes sense inside the block */
.generation-card__heading { ... }
.generation-card__body { ... }
.generation-card__send-btn { ... }

/* Modifier — a variant of the block or element */
.generation-card--full-width { ... }
.generation-card--placeholder { ... }
.generation-card__heading--muted { ... }
```

**Rules:**

1. **One Block per component.** The Block name describes what it IS, not where
   it lives. `.generation-card`, not `.left-panel-card`.

2. **Elements use `__` (double underscore).** An element only makes sense inside
   its Block. Never nest elements: `.card__header__title` is wrong — use
   `.card__title` instead (flatten the hierarchy).

3. **Modifiers use `--` (double hyphen).** Applied alongside the base class:
   `<div class="btn btn--primary">`, never `<div class="btn--primary">` alone.

4. **No tag selectors inside BEM.** Don't write `.card h3 { ... }` — use
   `.card__heading { ... }` so the HTML tag can change freely.

5. **Max two levels.** Block + Element is the deepest nesting. If you need
   sub-elements, create a new Block.

#### Flat Names (Layout Wiring)

```css
/* Page-specific spatial arrangements — no BEM needed */
.users-split { ... }
.dashboard-left { ... }
.api-builder-layout { ... }
.generation-class-grid { ... }
.favorites-layout { ... }
```

Layout classes typically only set:
- `display: grid` / `flex` and template columns/rows
- `gap`
- `align-items` / `justify-content`
- Responsive breakpoint overrides

They should NOT set colours, fonts, borders, or shadows — that's component
territory.

#### State Classes (`.is-*`)

All dynamic state uses the `.is-*` prefix. State classes are always applied
via JavaScript, never in static HTML.

```css
/* Correct */
.tab.is-active { ... }
.modal.is-visible { ... }
.btn.is-loading { ... }
.table-row.is-selected { ... }
.panel.is-collapsed { ... }

/* Wrong — don't use bare state names */
.tab.active { ... }     /* collides with HTML attributes */
.modal.visible { ... }  /* ambiguous */
.selected { ... }       /* too generic, no block context */
```

**Common state classes:**

| Class | Meaning |
|-------|---------|
| `.is-active` | Currently selected/focused (tabs, nav, toggles) |
| `.is-visible` | Shown (modals, dropdowns, tooltips) |
| `.is-selected` | User has selected this item (table rows, list items) |
| `.is-loading` | Async operation in progress |
| `.is-disabled` | Programmatically disabled (prefer `[disabled]` for form elements) |
| `.is-collapsed` | Collapsed/minimised section |
| `.is-modified` | Value differs from original/baseline |

#### Utility Classes (`.u-*` and `.hidden`)

Small, single-purpose overrides. Use sparingly.

```css
.u-sr-only { ... }    /* screen-reader only */
.u-muted { ... }      /* muted text colour */
.u-nowrap { ... }     /* no line wrapping */
.u-mono { ... }       /* force monospace font */
.hidden { ... }       /* display: none (the one exception to .u-* prefix) */
```

#### Summary Table

| What | Convention | Example |
|------|-----------|---------|
| Component root | BEM Block | `.generation-card` |
| Component child | BEM Element (`__`) | `.generation-card__heading` |
| Component variant | BEM Modifier (`--`) | `.generation-card--full-width` |
| Dynamic state | `.is-*` prefix | `.tab.is-active` |
| Layout arrangement | Flat descriptive | `.users-split`, `.api-builder-layout` |
| Utility override | `.u-*` prefix | `.u-sr-only`, `.u-muted` |
| Token variable | `--col-*`, `--sp-*`, etc. | `--col-accent`, `--sp-2` |

#### Naming in Practice — Before and After

Current name generator classes mapped to BEM:

| Current (flat) | BEM equivalent |
|---|---|
| `.generation-card` | `.generation-card` (already a Block) |
| `.generation-card h3` | `.generation-card__heading` |
| `.generation-card p` | `.generation-card__description` |
| `.generation-card .generation-send-btn` | `.generation-card__send-btn` |
| `.generation-card-full-width` | `.generation-card--full-width` |
| `.generation-placeholder` | `.generation-card--placeholder` |
| `.generation-class-grid` | `.generation-class-grid` (layout — stays flat) |
| `.api-builder-layout` | `.api-builder-layout` (layout — stays flat) |
| `.api-builder-pane` | `.api-builder-pane` (Block) |
| `.api-builder-pane h4` | `.api-builder-pane__heading` |
| `.preview-table__row:hover td` | `.preview-table__row:hover .preview-table__cell` |

Current MUD admin classes mapped to BEM:

| Current (flat) | BEM equivalent |
|---|---|
| `.detail-card` | `.detail-card` (Block) |
| `.detail-card h3` | `.detail-card__heading` |
| `.detail-list dt` | `.detail-list__label` |
| `.detail-list dd` | `.detail-list__value` |
| `.tab-button` | `.tab-button` (Block) |
| `.tab-button.is-active` | `.tab-button.is-active` (already correct) |
| `.status-pill` | `.status-pill` (Block) |
| `.status-pill.is-online` | `.status-pill.is-online` (already correct) |
| `.users-split` | `.users-split` (layout — stays flat) |
| `.dashboard-split` | `.dashboard-split` (layout — stays flat) |

### 8.3 Layer Order in Base CSS

1. Reset
2. Tokens (`:root`)
3. Light theme overrides
4. Global styles
5. App shell
6. Components (buttons, inputs, tables, cards, badges, modals, code)
7. Utilities
8. Accessibility
9. Responsive

---

## 9. Accessibility

1. **Focus rings:** `outline: 2px solid var(--col-accent); outline-offset: 2px` on `:focus-visible`
2. **Contrast:** >= 4.5:1 for all text
3. **Reduced motion:** All animations disabled via `prefers-reduced-motion`
4. **Screen reader:** `.u-sr-only` utility
5. **Touch targets:** Minimum 32x32px for interactive elements

---

## 10. Do's and Don'ts

### Do

- Use BEM for components (`block__element--modifier`)
- Use flat descriptive names for layout classes
- Use `.is-*` for all dynamic state classes
- Use CSS custom properties for all colours, fonts, and spacing
- Use the `--col-` prefix for colour tokens
- Use `color-mix()` for transparent borders and subtle backgrounds
- Test both dark and light themes
- Use `font-variant-numeric: tabular-nums` for numeric columns

### Don't

- Use bare state class names (`.active`, `.selected`) — always `.is-*`
- Nest BEM elements (`.card__header__title`) — flatten to `.card__title`
- Use a BEM modifier without the base class (`class="btn--primary"` alone)
- Write tag selectors inside components (`.card h3`) — use `.card__heading`
- Set colours, fonts, or borders in layout classes — that's component territory
- Hardcode colour values — always use tokens
- Use `!important` except for utilities (`.hidden`, `.u-sr-only`)
- Use `border-radius` > 12px
- Import external CSS frameworks
- Apply editorial fonts (serif stack) to interactive app elements

---

## 11. Relationship to Editorial System

The pipe-works.org website uses a completely separate visual language:

| Aspect | App Tools (this guide) | Website (editorial guide) |
|--------|----------------------|--------------------------|
| **Mood** | Dark industrial dashboard | Aged broadsheet pinned to a wall |
| **Primary font** | Monospace (JetBrains Mono stack) | Serif (Crimson Text, Libre Baskerville) |
| **Colour palette** | Grey + amber on dark | Ink + blood on aged paper |
| **Theme toggle** | Yes (dark/light) | No (single aesthetic) |
| **Layout** | Panels, grids, data tables | Centred `.sheet` with quirk transforms |
| **Token prefix** | `--col-*` | `--ink-*`, `--paper-*` |

They share the same **font files** (woff2) but use them for entirely different purposes.
The editorial guide lives at [`../editorial/STYLE_GUIDE.md`](../editorial/STYLE_GUIDE.md).
