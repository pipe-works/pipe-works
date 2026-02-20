# Migration Notes — Adopting pipe-works-base.css

## Overview

This document describes how to migrate existing Pipe-Works app-mode projects from
their current CSS to the unified `pipe-works-base.css` + `pipe-works-fonts.css`.

---

## File Inventory

| File | Purpose |
|------|---------|
| `pipe-works-base.css` | Design tokens, reset, common components |
| `pipe-works-fonts.css` | @font-face declarations (self-hosted woff2) |
| `STYLE_GUIDE.md` | Design system documentation |
| `MIGRATION_NOTES.md` | This file |
| `TOKEN_MAP.md` | Variable name mapping between projects |

---

## Migration by Project

### 1. Axis Descriptor Lab (`pipeworks_axis_descriptor_lab`)

**Status:** Migrated (PR [#37](https://github.com/pipe-works/pipeworks_axis_descriptor_lab/pull/37))
**Effort:** Low

**What was done:**

1. Copied `pipe-works-fonts.css`, `pipe-works-base.css`, and 16 woff2 font files
   into `app/static/`
2. Added `<link>` tags for fonts and base CSS before `styles.css` in the Jinja2
   template (`index.html`)
3. Removed ~650 lines from `styles.css` now covered by the base: reset, design
   tokens, global styles, app-header/title/subtitle, panel/panel__heading,
   control-label/control-row, inputs/select/code-editor, buttons, badges,
   range-input, output-box, toggle-label/toggle-text, divider, status-bar,
   spinner, utilities (hidden, placeholder-text), scrollbar, tooltip
   bubble/arrow, and their light-theme overrides
4. Added `position: fixed` overrides for `.app-header` and `.status-bar` (base
   uses `flex-shrink: 0` for flex layouts; the lab's three-column fixed grid
   requires fixed positioning)
5. Replaced hardcoded colours with tokens: `--col-code-bg`, `--col-border-hi`,
   `--col-accent-glow`, `--col-backdrop`, `color-mix()` for semi-transparent
   borders
6. Renamed `--tooltip-*` → `--col-tooltip-*` in `mod-tooltip.js` (2 references)
7. Fixed `--fs-sm` typo → `--text-sm` in `.input--url`
8. Reduced light-theme overrides to 2 app-specific rules (`.tmap-indicator`)

**Result:** `styles.css` reduced from 1411 to 759 lines. No visual changes.

**Lessons for other migrations:**

- The base CSS `.app-header` and `.status-bar` use `flex-shrink: 0`, which
  assumes a flex-parent shell. Projects using `position: fixed` layouts need
  to re-add positioning in their app-specific CSS.
- The base CSS `.divider` adds `margin: var(--sp-3) 0` — check whether this
  affects spacing in your app before extracting.
- The base CSS spinner uses `@keyframes pw-spin` (not `spin`) — search for
  any JS references to the animation name.
- `color-mix(in srgb, var(--token) N%, transparent)` is a clean replacement
  for hardcoded `rgba()` values that need to adapt to theme switching.
- The base CSS global monospace rule (`h1–h6, button, input, select, textarea,
  table, code { font-family: var(--font-mono) }`) had no impact on the lab
  because it already applied monospace per-class, but projects that rely on
  inheriting `--font-ui` for these elements will need explicit overrides.

---

### 2. Name Generator (`pipeworks_name_generation`)

**Status:** Migrated (PR [#86](https://github.com/pipe-works/pipeworks_name_generation/pull/86))
**Effort:** Medium

**What was done:**

1. Copied `pipe-works-fonts.css`, `pipe-works-base.css`, and 16 woff2 font files
   into `pipeworks_name_generation/webapp/frontend/static/`
2. Added `<link>` tags for fonts and base CSS before `app.css` in the Jinja2-style
   template (`index.html`)
3. Registered the two new CSS files in the webapp's explicit route registry
   (`route_registry.py`, `endpoint_adapters.py`, `assets.py`) — the server uses
   manual route dispatch, not a static directory mount
4. Removed ~290 lines from `app.css` now covered by the base: `@font-face` blocks,
   `:root` dark tokens, `body[data-theme="light"]` light tokens, body/focus-visible
   base styles, `.app-header`/`.app-main`/`.status-bar` shell styles, raw element
   selectors (`button`, `input`, `select`, `table`, `th`, `td`, `ul`, `li`, `code`,
   `h1`), `input[type="checkbox"]`/`input[type="range"]` styling, `.section-divider`,
   scrollbar styles, and all light-theme overrides
5. Renamed 67 CSS variable references from unprefixed to canonical `--col-*` tokens
6. Updated theme toggle JS: `document.body.dataset.theme` →
   `document.documentElement.dataset.theme` (2 lines in `app.js`)
7. Added component classes throughout HTML and JS:
   - `btn btn--primary` on ~30 action buttons
   - `btn btn--secondary btn--sm` on theme toggle
   - `btn btn--icon` on toggle/nav/close buttons
   - `btn btn--primary btn--sm` on copy/fav/export buttons
   - `class="input"` on text/number inputs and textareas
   - `class="select"` on all select elements
   - `class="range-input"` on range inputs
   - `class="divider"` replacing `.section-divider`
8. Updated dynamically-created buttons in `favorites.js` with `btn btn--primary`
9. Refactored help panel entries to use base `.card` component with BEM children
   (`.help-entry__question`, `.help-entry__answer`) using `--font-heading` and
   `--font-body` for visual hierarchy

**Result:** `app.css` reduced from 1137 to ~850 lines. All 2,405 tests pass.

**Lessons for other migrations:**

- **Explicit route registries:** The name generator webapp uses manual HTTP route
  dispatch (not a catch-all static directory). New CSS files needed route entries,
  endpoint adapter functions, and content-type whitelist entries in `assets.py`.
  Any project with explicit route registration will hit this — check how static
  files are actually served, not just whether the files exist on disk.
- **Base `.panel` naming collision:** Base CSS `.panel` provides background, padding,
  flex layout, and gap — but the name generator uses `.panel` purely for tab content
  show/hide (`display: none`). Fixed by overriding in app.css:
  `display: none; background: transparent; padding: 0; overflow-y: visible;`
  Projects reusing `.panel` for non-standard purposes will need similar overrides.
- **Button variants required for visibility:** After the base button reset
  (`background: none; border: 0; padding: 0`), buttons without a variant class
  (e.g., `btn btn--sm` with no `--primary`/`--secondary`) are invisible. Always
  pair `.btn` with a variant.
- **Range inputs need `.range-input` class:** Base CSS uses `.range-input` (class
  selector), not `input[type="range"]` (attribute selector). Range inputs without
  the class get no styling.
- **Theme toggle button styling:** `btn btn--ghost` has no border. If the toggle
  needs a visible border, use `btn btn--secondary btn--sm` instead.
- **Modal naming:** The name generator uses hyphenated modal classes
  (`.modal-backdrop`, `.modal-card`) rather than BEM (`.modal__backdrop`,
  `.modal__card`). This was kept as-is — a future pass could align to BEM.
- **`var(--col-backdrop)` eliminates light-theme overrides:** The modal backdrop
  used a hardcoded `rgba()` with a separate light-theme override. Replacing with
  `var(--col-backdrop)` handles both themes in one rule.
- **Body flex layout not in base:** Base CSS body doesn't include
  `display: flex; flex-direction: column; overflow: hidden;` needed for full-height
  app shells. Add as an app-specific override.

**Deferred items:**

- State class BEM migration (`.active` → `.is-active`, `.collapsed` →
  `.is-collapsed`) — low priority, no functional impact
- Modal BEM alignment (`.modal-backdrop` → `.modal__backdrop`) — kept hyphenated
  names for now

---

### 3. MUD Server Admin (`pipeworks_mud_server`)

**Status:** Not started — needs full aesthetic alignment.
**Effort:** High
**Scope:** Admin shell only — the play UI is separate and excluded.

The MUD server admin shell currently uses a SaaS-style design (blue accent,
light-default, rounded corners, Sora font) that diverges significantly from the
Pipe-Works app tools aesthetic. This section documents the full alignment plan.

#### Current CSS Architecture

The admin loads 7 CSS files in this order:

```
base.css       — Reset, root font, layout max-width
themes.css     — --color-* tokens (light default, dark override)
layout.css     — App shell: sidebar + content grid, header, navigation
components.css — Cards, panels, detail views, tags, status pills, schema
forms.css      — Form inputs, labels, buttons, error states
admin.css      — Admin-specific: tables, users split, dashboard, tabs
toasts.css     — Toast notification system
```

#### Phase 1: Token Migration

Rename all `--color-*` variables to `--col-*` and swap palette values.

| Current (`themes.css`) | New (from `pipe-works-base.css`) |
|---|---|
| `--color-bg: #e9edf4` | `--col-bg: #f4f1ec` (light) / `#111214` (dark) |
| `--color-bg-alt: #f5f7fb` | Map to `--col-surface` or `--col-surface-2` |
| `--color-surface: #ffffff` | `--col-surface: #faf8f5` (light) / `#1c1e22` (dark) |
| `--color-surface-raised: #ffffff` | `--col-surface-2: #efece6` (light) / `#24272d` (dark) |
| `--color-sidebar: #eef3f9` | Map to `--col-surface` |
| `--color-text: #121418` | `--col-text: #2c2a26` (light) / `#d4d7dc` (dark) |
| `--color-muted: #5a6372` | `--col-text-muted: #7a7568` (light) / `#6b7280` (dark) |
| `--color-border: #d6dbe3` | `--col-border: #d6d0c6` (light) / `#2e3138` (dark) |
| `--color-accent: #2563eb` | `--col-accent: #c27b0a` (light) / `#f59e0b` (dark) |
| `--color-danger: #c0392b` | `--col-err: #dc2626` (light) / `#ef4444` (dark) |
| `--color-success: #1d7a3a` | `--col-ok: #16a34a` (light) / `#22c55e` (dark) |
| `--shadow-soft` | Remove or reduce (app tools use minimal shadows) |

**Important:** Flip the default theme. Currently `themes.css` defines light as
default with `html[data-theme="dark"]` as override. The base CSS uses dark as
default with `[data-theme="light"]` as override.

#### Phase 2: Typography Alignment

1. Remove "Sora" font dependency
2. Import `pipe-works-fonts.css`
3. Apply `--font-mono` to headings, buttons, inputs, tables, code (per base CSS)
4. Apply `--font-ui` to body text and descriptions
5. Reduce base font size from `16px` to `0.875rem` (14px)

#### Phase 3: Geometry Alignment

| Property | Current | Target |
|----------|---------|--------|
| Card border-radius | 16–20px | 8–12px (`--radius-md`, `--radius-lg`) |
| Button border-radius | 10px | 4px (`--radius-sm`) |
| Input border-radius | 10px | 4px (`--radius-sm`) |
| Card padding | 1.5–2.75rem | 0.75–0.85rem |
| Tab buttons | 999px (pill) | 4px (`--radius-sm`) |
| Status pill | 999px (pill) | 3px (badge style) |

#### Phase 4: Component Class Adoption

Replace project-specific component patterns with base CSS classes:

| Current Class | Replace With |
|---|---|
| `.actions button` | `.btn .btn--secondary` |
| `.form button`, `.detail-form button` | `.btn .btn--primary` |
| `.theme-toggle`, `.logout` | `.btn .btn--ghost` |
| `.character-actions button` | `.btn .btn--secondary .btn--sm` |
| `.form input`, `.detail-form input` | `.input` |
| `.detail-form select` | `.select` |
| `.card` | `.card` (adjust padding/radius) |
| `.detail-card` | `.card .card--compact` |
| `.kpi-card` | `.card .card--compact` |
| `.status-pill` | `.badge` variants |
| `.tab-button` | `.tab` (from base, or define) |
| `.toast` | Keep as-is (unique component) |

#### Phase 5: Layout Decisions

The admin's **sidebar layout** is appropriate for a management dashboard and
doesn't need to change to a header-based shell. However:

1. Adopt base CSS tokens for all colours, spacing, and typography
2. Consider using `--header-h` for the sticky header height
3. Use base CSS scrollbar styles
4. Apply `.panel` styling conventions to sidebar

#### Admin-Specific CSS After Migration

After alignment, the admin's CSS files should consolidate to:

```html
<!-- Shared -->
<link rel="stylesheet" href="pipe-works-fonts.css">
<link rel="stylesheet" href="pipe-works-base.css">

<!-- Admin-specific (what remains) -->
<link rel="stylesheet" href="admin.css">
```

The admin-specific CSS should only contain:

- Sidebar layout (unique to admin)
- Table enhancements (sortable, selectable rows, zebra striping)
- Users/dashboard split layouts
- Schema visualisation
- Toast notifications
- Character creation panels
- Any admin-only component patterns

---

### 4. Pipe-Works Website (`pipe-works-org`)

**Status:** Different aesthetic — no migration to app base CSS.

The website uses an editorial/print-workshop aesthetic that is intentionally
distinct from the app-mode tools. It has its own style guide at
[`../editorial/STYLE_GUIDE.md`](../editorial/STYLE_GUIDE.md).

The editorial font tokens (`--font-masthead`, `--font-headline`, etc.) are
included in the app base CSS so apps can use branded typography when needed.

---

### 5. Future Projects

New Pipe-Works tool projects should:

1. Copy `pipe-works-fonts.css` and adjust font paths
2. Import `pipe-works-base.css` as the foundation
3. Write app-specific CSS using the token system
4. Use the class-based component system (`.btn`, `.input`, `.card`, etc.)

---

## Breaking Changes Checklist

When migrating any project, check for these potential issues:

- [x] **Raw element selectors** — Base CSS applies `font-family: --font-mono` to
  all headings, buttons, inputs, tables, and code. If your app relies on
  inheriting `--font-ui` for these elements, add explicit overrides.
  *Axis Descriptor Lab: no impact — already monospace per-class.*
  *Name Generator: no impact — already monospace-dominant.*

- [x] **Theme toggle direction** — Base CSS uses dark as default with
  `[data-theme="light"]` on `<html>` as override. Projects that default to light
  (MUD server admin) must flip their theme toggle logic.
  *Axis Descriptor Lab: already dark-default.*
  *Name Generator: already dark-default. Changed `document.body.dataset.theme`
  to `document.documentElement.dataset.theme` (2 lines in app.js).*

- [x] **Light theme selector** — Base CSS uses `[data-theme="light"]` on `<html>`.
  The name generator used `body[data-theme="light"]`. The MUD server admin uses
  `html[data-theme="dark"]`. All must standardise to `<html>` with light as the
  non-default state.
  *Axis Descriptor Lab: already uses `html[data-theme="light"]`.*
  *Name Generator: migrated from `body` to `html`. All light-theme overrides
  removed from app.css (handled by base CSS).*

- [x] **Reset aggressiveness** — Base CSS zeroes all margins and padding on
  `*, *::before, *::after`. If your app relies on default browser margins for
  `<p>`, `<h1>`, `<ul>`, etc., add explicit margins.
  *Axis Descriptor Lab: already had identical reset.*
  *Name Generator: already had identical reset.*

- [x] **List style** — Base CSS sets `list-style: none` on `<ul>` and `<ol>`.
  Add `list-style: disc` (or `square`) explicitly where needed.
  *Axis Descriptor Lab: no lists in the SPA.*
  *Name Generator: added `list-style: disc` to `.help-entry ul`.*

- [x] **Button reset** — Base CSS resets `<button>` to `background: none;
  border: 0; padding: 0`. All buttons must use `.btn` classes for styling.
  *Axis Descriptor Lab: all buttons already use `.btn` or custom classes
  (`.theme-toggle`, `.tooltip-toggle`).*
  *Name Generator: added `.btn` + variant classes to ~30 static buttons in
  HTML and 2 dynamically-created buttons in JS. Important: always pair `.btn`
  with a variant (`--primary`, `--secondary`, `--ghost`, `--icon`) — without
  a variant, buttons are invisible after reset.*

- [ ] **Accent colour** — Projects using blue accent (`#2563eb`) must switch to
  amber (`#f59e0b` dark / `#c27b0a` light). Search for hardcoded blue values
  in both CSS and JavaScript (e.g., `rgba(37, 99, 235, ...)` in the MUD admin).

- [ ] **Shadow removal** — The app tools aesthetic uses minimal shadows. Projects
  with `box-shadow: var(--shadow-soft)` on every card should remove or reduce
  shadows to match.

- [x] **`color-mix()` support** — Used for transparent borders. Requires
  Chrome 111+, Firefox 113+, Safari 16.2+. All current browsers support it.
  *Axis Descriptor Lab: adopted `color-mix()` for meta-table, meta-copy-btn,
  and tmap-indicator borders.*
  *Name Generator: already used `color-mix()` — no issues.*

- [x] **`.divider` margin** — Base CSS adds `margin: var(--sp-3) 0` to
  `.divider`. Projects with tighter spacing may need to override.
  *Axis Descriptor Lab: no impact — dividers are inside flex panels that
  control spacing via `gap`.*
  *Name Generator: renamed `.section-divider` to `.divider`. No spacing issues.*

- [x] **Spinner keyframe name** — Base CSS uses `@keyframes pw-spin` instead
  of `spin`. Search for JS references to the animation name.
  *Axis Descriptor Lab: no JS references found.*
  *Name Generator: no spinner usage — no impact.*

- [x] **`position: fixed` shell components** — Base CSS `.app-header` and
  `.status-bar` use `flex-shrink: 0` (for flex-parent layouts). Projects
  using fixed-position layouts must re-add `position: fixed` and coordinates.
  *Axis Descriptor Lab: added overrides in app-specific CSS.*
  *Name Generator: uses flex layout — no override needed. Added
  `body { display: flex; flex-direction: column; overflow: hidden; }` as
  the base CSS body doesn't include this.*

- [x] **`.panel` naming collision** — Base CSS `.panel` provides background,
  padding, flex layout, and gap. Projects that use `.panel` for tab content
  show/hide (where `display: none` is toggled by JS) must override the base
  styles to neutralise them.
  *Axis Descriptor Lab: no `.panel` usage.*
  *Name Generator: added override:
  `.panel { display: none; background: transparent; padding: 0; }`*

- [x] **Range input class selector** — Base CSS uses `.range-input` (class),
  not `input[type="range"]` (attribute). Range inputs without the class get
  no styling.
  *Axis Descriptor Lab: no range inputs.*
  *Name Generator: added `class="range-input"` to both range inputs.*

- [x] **Explicit route registration for new CSS files** — Projects with
  manual HTTP route dispatch (not a catch-all static directory) need route
  entries, endpoint adapters, and content-type whitelist entries for the new
  CSS files. Files existing on disk is not enough — verify the server
  actually serves them.
  *Axis Descriptor Lab: uses Jinja2 + standard static mounting — no issue.*
  *Name Generator: required additions to `route_registry.py`,
  `endpoint_adapters.py`, and `assets.py`.*

---

## Recommended Import Order

```html
<!-- 1. Font declarations (cacheable, rarely changes) -->
<link rel="stylesheet" href="/static/pipe-works-fonts.css">

<!-- 2. Base design system (tokens, reset, components) -->
<link rel="stylesheet" href="/static/pipe-works-base.css">

<!-- 3. App-specific styles -->
<link rel="stylesheet" href="/static/app.css">
```

---

## Font File Directory Structure

Each project needs the following woff2 files in its font directory:

```
fonts/
├── CourierPrime-Regular.woff2
├── CourierPrime-Italic.woff2
├── CourierPrime-Bold.woff2
├── CourierPrime-BoldItalic.woff2
├── CrimsonText-Regular.woff2
├── CrimsonText-Italic.woff2
├── CrimsonText-SemiBold.woff2
├── CrimsonText-SemiBoldItalic.woff2
├── CrimsonText-Bold.woff2
├── CrimsonText-BoldItalic.woff2
├── IMFellEnglish-Regular.woff2
├── IMFellEnglish-Italic.woff2
├── IMFellEnglishSC-Regular.woff2
├── LibreBaskerville-VariableFont_wght.woff2
├── LibreBaskerville-Italic-VariableFont_wght.woff2
└── SpecialElite-Regular.woff2
```

Total: 16 files, approximately 500KB combined.

---

## BEM Adoption

All migrations should adopt the BEM naming convention documented in
`STYLE_GUIDE.md` section 8.2. In summary:

- **Components** use BEM: `.card__heading`, `.btn--primary`
- **Layout** stays flat: `.users-split`, `.api-builder-layout`
- **State** uses `.is-*`: `.tab.is-active`, `.modal.is-visible`
- **Tag selectors inside components are removed**: `.card h3` becomes `.card__heading`

This can be done incrementally — rename classes in HTML and CSS together,
one component at a time.

---

## Migration Priority

| Project | Effort | Priority | Status |
|---------|--------|----------|--------|
| Axis Descriptor Lab | Low | 1st | **Done** — [PR #37](https://github.com/pipe-works/pipeworks_axis_descriptor_lab/pull/37) |
| Name Generator | Medium | 2nd | **Done** — [PR #86](https://github.com/pipe-works/pipeworks_name_generation/pull/86) |
| MUD Server Admin | High | 3rd | Not started |
