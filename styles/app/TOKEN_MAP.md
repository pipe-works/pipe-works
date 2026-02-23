# Token Map — Variable Name Mapping

Cross-reference of CSS custom property names across all Pipe-Works app-mode projects.

> The website (editorial) uses a completely separate token system (`--ink-*`, `--paper-*`)
> and is not included here. See [`../editorial/STYLE_GUIDE.md`](../editorial/STYLE_GUIDE.md).

### Migration Status

| Project | Status | Notes |
|---|---|---|
| Axis Descriptor Lab | **Migrated** | Imports `pipe-works-base.css` directly. All tokens canonical. |
| Name Generator | **Migrated** | Imports `pipe-works-base.css` directly. All tokens canonical. |
| Syllable Walk Web | **Migrated** | Imports `pipe-works-base.css` directly. All tokens canonical. |
| MUD Server Admin | **Migrated** | Imports `pipe-works-base.css` directly. All tokens canonical. |
| Image Generator | **Migrated** | Imports `pipe-works-base.css` directly. All tokens canonical. Zero custom properties in `app.css`. |

---

## Colour Tokens

| Base CSS (canonical) | Axis Descriptor Lab | Name Generator | Syllable Walk Web | MUD Server Admin | Image Generator |
|---|---|---|---|---|---|
| `--col-bg` | `--col-bg` | `--col-bg` | `--col-bg` (via base) | `--col-bg` (via base) | `--col-bg` (via base) |
| `--col-surface` | `--col-surface` | `--col-surface` | `--col-surface` | `--col-surface` (via base) | `--col-surface` (via base) |
| `--col-surface-2` | `--col-surface-2` | `--col-surface-2` | `--col-surface-2` | `--col-surface-2` (via base) | `--col-surface-2` (via base) |
| `--col-border` | `--col-border` | `--col-border` | `--col-border` | `--col-border` (via base) | `--col-border` (via base) |
| `--col-border-hi` | `--col-border-hi` | `--col-border-hi` | `--col-border-hi` (via base) | `--col-border-hi` (via base) | — |
| `--col-text` | `--col-text` | `--col-text` | `--col-text` | `--col-text` (via base) | `--col-text` (via base) |
| `--col-text-muted` | `--col-text-muted` | `--col-text-muted` | `--col-text-muted` | `--col-text-muted` (via base) | `--col-text-muted` (via base) |
| `--col-text-dim` | `--col-text-dim` | `--col-text-dim` | `--col-text-dim` | `--col-text-dim` (via base) | `--col-text-dim` (via base) |
| `--col-accent` | `--col-accent` | `--col-accent` | `--col-accent` | `--col-accent` (via base) | `--col-accent` (via base) |
| `--col-accent-dim` | `--col-accent-dim` | `--col-accent-dim` | `--col-accent-dim` (via base) | `--col-accent-dim` (via base) | `--col-accent-dim` (via base) |
| `--col-accent-glow` | `--col-accent-glow` | `--col-accent-glow` | `--col-accent-glow` | `--col-accent-glow` (via base) | — |
| `--col-ok` | `--col-ok` | `--col-ok` | `--col-ok` | `--col-ok` (via base) | `--col-ok` (via base) |
| `--col-err` | `--col-err` | `--col-err` | `--col-err` | `--col-err` (via base) | `--col-err` (via base) |
| `--col-warn` | `--col-warn` | — | `--col-warn` | — | `--col-warn` (via base) |
| `--col-info` | `--col-info` | — | — | — | `--col-info` (via base) |
| `--col-code-bg` | `--col-code-bg` | `--col-code-bg` | `--col-code-bg` | `--col-code-bg` (via base) | `--col-code-bg` (via base) |
| `--col-code-text` | `--col-code-text` | `--col-code-text` | `--col-code-text` (via base) | `--col-code-text` (via base) | — |
| `--col-code-inline` | `--col-code-inline` | `--col-code-inline` | — | — | — |
| `--col-button-text` | `--col-button-text` | `--col-button-text` | `--col-button-text` | `--col-button-text` (via base) | `--col-button-text` (via base) |
| `--col-backdrop` | `--col-backdrop` | `--col-backdrop` | `--col-backdrop` (via base) | — | — |
| `--col-tooltip-bg` | `--col-tooltip-bg` | — | — | — | — |
| `--col-tooltip-text` | `--col-tooltip-text` | — | — | — | — |
| `--col-tooltip-border` | `--col-tooltip-border` | — | — | — | — |
| `--col-diff-add` | `--col-diff-add` | — | — | — | — |
| `--col-diff-del` | `--col-diff-del` | — | — | — | — |
| `--col-diff-add-text` | `--col-diff-add-text` | — | — | — | — |
| `--col-diff-del-text` | `--col-diff-del-text` | — | — | — | — |

---

## Typography Tokens

| Base CSS (canonical) | Axis Descriptor Lab | Name Generator | Syllable Walk Web | MUD Server Admin | Image Generator |
|---|---|---|---|---|---|
| `--font-mono` | `--font-mono` | `--font-mono` (via base) | `--font-mono` | `--font-mono` (via base) | `--font-mono` (via base) |
| `--font-ui` | `--font-ui` | `--font-ui` (via base) | `--font-ui` (via base) | `--font-ui` (via base) | `--font-ui` (via base) |
| `--font-heading` | `--font-heading` (via base) | `--font-heading` (via base) | `--font-heading` (via base) | `--font-heading` (via base) | `--font-heading` (via base) |
| `--font-body` | `--font-body` (via base) | `--font-body` (via base) | `--font-body` (via base) | `--font-body` (via base) | `--font-body` (via base) |
| `--font-masthead` | `--font-masthead` (via base) | `--font-masthead` (via base) | `--font-masthead` (via base) | `--font-masthead` (via base) | `--font-masthead` (via base) |
| `--font-headline` | `--font-headline` (via base) | `--font-headline` (via base) | `--font-headline` (via base) | `--font-headline` (via base) | `--font-headline` (via base) |
| `--font-record` | `--font-record` (via base) | `--font-record` (via base) | `--font-record` (via base) | `--font-record` (via base) | `--font-record` (via base) |
| `--font-symbols` | `--font-symbols` (via base) | `--font-symbols` (via base) | `--font-symbols` (via base) | `--font-symbols` (via base) | `--font-symbols` (via base) |
| `--font-accent` | `--font-accent` (via base) | `--font-accent` (via base) | `--font-accent` (via base) | `--font-accent` (via base) | `--font-accent` (via base) |

---

## Type Scale Tokens

| Base CSS (canonical) | Axis Descriptor Lab | Name Generator | Syllable Walk Web | MUD Server Admin | Image Generator |
|---|---|---|---|---|---|
| `--text-xs` (`0.70rem`) | `--text-xs` | `--text-xs` (via base) | `--text-xs` | `--text-xs` (via base) | `--text-xs` (via base) |
| `--text-sm` (`0.80rem`) | `--text-sm` | `--text-sm` (via base) | `--text-sm` | `--text-sm` (via base) | `--text-sm` (via base) |
| `--text-base` (`0.875rem`) | `--text-base` | `--text-base` (via base) | `--text-base` | `--text-base` (via base) | `--text-base` (via base) |
| `--text-lg` (`1.0rem`) | `--text-lg` | `--text-lg` (via base) | `--text-lg` (via base) | `--text-lg` (via base) | — |
| `--text-xl` (`1.15rem`) | `--text-xl` | `--text-xl` (via base) | `--text-xl` | `--text-xl` (via base) | — |

---

## Spacing Tokens

| Base CSS (canonical) | Axis Descriptor Lab | Name Generator | Syllable Walk Web | MUD Server Admin | Image Generator |
|---|---|---|---|---|---|
| `--sp-1` (`0.25rem`) | `--sp-1` | `--sp-1` (via base) | `--sp-1` | `--sp-1` (via base + admin.css) | `--sp-1` (via base) |
| `--sp-2` (`0.5rem`) | `--sp-2` | `--sp-2` (via base) | `--sp-2` | `--sp-2` (via base + admin.css) | `--sp-2` (via base) |
| `--sp-3` (`0.75rem`) | `--sp-3` | `--sp-3` (via base) | `--sp-3` | `--sp-3` (via base + admin.css) | `--sp-3` (via base) |
| `--sp-4` (`1rem`) | `--sp-4` | `--sp-4` (via base) | `--sp-4` | `--sp-4` (via base + admin.css) | `--sp-4` (via base) |
| `--sp-6` (`1.5rem`) | `--sp-6` | `--sp-6` (via base) | `--sp-6` (via base) | `--sp-6` (via base + admin.css) | `--sp-6` (via base) |

---

## Layout Tokens

| Base CSS (canonical) | Axis Descriptor Lab | Name Generator | Syllable Walk Web | MUD Server Admin | Image Generator |
|---|---|---|---|---|---|
| `--header-h` (`2.75rem`) | `--header-h` | `--header-h` (via base) | `--header-h` (overridden to `auto`) | — (uses sidebar layout) | `--header-h` (via base) |
| `--statusbar-h` (`1.75rem`) | `--statusbar-h` | `--statusbar-h` (via base) | `--statusbar-h` (via base) | — (no status bar) | `--statusbar-h` (via base) |
| `--panel-pad` (`1rem`) | `--panel-pad` | `--panel-pad` (via base) | `--panel-pad` | `--panel-pad` (via base) | — |
| `--radius-sm` (`4px`) | `--radius-sm` | `--radius-sm` (via base) | `--radius-sm` | `--radius-sm` (via base + admin.css) | `--radius-sm` (via base) |
| `--radius-md` (`8px`) | `--radius-md` | `--radius-md` (via base) | `--radius-md` | `--radius-md` (via base + admin.css) | `--radius-md` (via base) |
| `--radius-lg` (`12px`) | `--radius-lg` | `--radius-lg` (via base) | `--radius-lg` (via base) | `--radius-lg` (via base + admin.css) | `--radius-lg` (via base) |

### MUD Server Admin — Layout Notes

The admin uses a **sidebar (220px) + content grid** pattern rather than the
header + status bar shell used by the Axis Descriptor Lab and Name Generator.
This is intentional — a sidebar is more appropriate for a multi-page management
dashboard. The layout is defined entirely in `admin.css` and uses base tokens
for all colours, spacing, radii, and typography. Default theme is dark.

### Image Generator — Layout Notes

The Image Generator uses a **header + tab navigation + sidebar/main split** pattern.
The header holds branding, prompt preview, stats, and theme toggle. A tab bar
switches between Generation, Gallery, Favourites, and Help views. The Generation
tab uses a `.gen-layout` grid: a 340px scrollable sidebar (`.gen-controls`) for
model selection, prompt composition, and image settings, plus a flexible main area
(`.gen-output`) for the output canvas. A status bar at the bottom shows generation
state, model name, and last seed. The layout is defined in `app.css` and uses base
tokens for all colours, spacing, radii, and typography. Default theme is dark.

### Syllable Walk Web — Layout Notes

The Syllable Walk Web uses a **two-tier header + status bar** pattern. The top
row holds branding, a tool switcher (Pipeline / Walker), and a theme toggle.
The bottom row shows context-dependent sub-screen tabs. `--header-h` is
overridden to `auto` to accommodate both rows. The main content area switches
between grid layouts (four-column walker, two-column pipeline) depending on the
active tool and sub-screen. The layout is defined in `app.css` and uses base
tokens for all colours, spacing, radii, and typography.

---

## Animation Tokens

| Base CSS (canonical) | Axis Descriptor Lab | Name Generator | Syllable Walk Web | MUD Server Admin | Image Generator |
|---|---|---|---|---|---|
| `--transition-fast` (`100ms ease`) | `--transition-fast` | `--transition-fast` (via base) | `--transition-fast` | `--transition-fast` (via base) | `--transition-fast` (via base) |
| `--transition-med` (`200ms ease`) | `--transition-med` | `--transition-med` (via base) | `--transition-med` | `--transition-med` (via base) | `--transition-med` (via base) |

---

## Component Class Mapping

| Base CSS | Axis Descriptor Lab | Name Generator | Syllable Walk Web | MUD Server Admin | Image Generator |
|---|---|---|---|---|---|
| `.btn` | `.btn` | `.btn` | `.btn` | `.btn` | `.btn` |
| `.btn--primary` | `.btn--primary` | `.btn--primary` | `.btn--primary` | `.btn--primary` (submit buttons) | `.btn--primary` (lightbox actions) |
| `.btn--secondary` | `.btn--secondary` | `.btn--secondary` | `.btn--secondary` | `.btn--secondary` (actions, refresh) | `.btn--secondary` (gallery toolbar) |
| `.btn--ghost` | `.btn--ghost` | — | `.btn--ghost` | — | `.btn--ghost` (header nav, tab close) |
| `.btn--sm` | `.btn--sm` | `.btn--sm` | `.btn--sm` | `.btn--sm` (kick, tombstone, delete) | `.btn--sm` (batch controls, clear) |
| `.btn--full` | — | — | `.btn--full` | `.btn--full` (login submit) | — |
| `.btn--icon` | — | `.btn--icon` | `.btn--icon` | — | `.btn--icon` (theme toggle, lightbox close) |
| `.input` | `.input` | `.input` | `.input` | `.input` | `.input` (seed input) |
| `.select` | `.select` | `.select` | `.select` | `.select` | `.select` (model, aspect ratio, prompts) |
| `.range-input` | — | `.range-input` | `.range-input` | — | `.range-input` (steps, guidance sliders) |
| `.code-editor` | `.code-editor` | — | — | — | — |
| `.badge` | `.badge` | — | `.badge` | `.badge` | `.badge` (batch number, model label) |
| `.badge--active` | `.badge--active` | — | — | `.badge--active` (online status) | — |
| `.badge--muted` | — | — | `.badge--muted` (idle/demo labels) | `.badge--muted` (offline status) | `.badge--muted` (resolution label) |
| `.card` | — | `.card` (help entries) | — | `.card` (table cards, dashboard) | — |
| `.u-muted` | — | — | `.u-muted` | `.u-muted` (replaced `.muted`) | `.u-muted` (help text, labels) |
| `.modal` | — | `.modal` | `.modal` | — | `.modal` (prompt preview, stats) |
| `.modal__backdrop` | — | `.modal-backdrop` (hyphenated) | `.modal__backdrop` (BEM) | — | `.modal__backdrop` (BEM) |
| `.modal__card` | — | `.modal-card` (hyphenated) | `.modal__card` (BEM) | — | `.modal__card` (BEM) |
| `.spinner` | `.spinner` | — | — | — | — |
| `.divider` | `.divider` | `.divider` | `.divider` | — | — |
| `.hidden` | `.hidden` | — | `.hidden` | — | `.hidden` |
| `.u-sr-only` | `.u-sr-only` (via base) | — | — | — | `.u-sr-only` (via base) |
| — | — | — | — | `.auth-panel` (login/loading states) | — |
| — | — | — | — | `.tag` (pill-shaped chip) | — |
| — | — | — | — | `.toast`, `.toast-container` | `.toast`, `.toast-container` (notifications) |
| — | — | `.tab`, `.tab.active` | `.tab`, `.tab.is-active` | `.tab-button`, `.tab-button.is-active` | `.tab-nav__item`, `.tab-nav__item.is-active` |
| — | — | — | — | — | `.btn--generate` (app-specific, accent shimmer) |
| — | — | — | — | — | `.img-card` (app-specific, gallery thumbnail) |
| — | — | — | — | — | `.lightbox` (app-specific, image detail modal) |
| — | — | — | — | — | `.gen-layout` (app-specific, sidebar + main grid) |
| — | — | — | — | — | `.prompt-textarea` (app-specific, prompt input) |

---

## Light Theme Values

Axis Descriptor Lab, Name Generator, and Syllable Walk Web all import
`pipe-works-base.css` directly and share identical palettes via canonical
tokens. The MUD Server Admin uses a completely different palette (see Colour
Value Differences above).

| Token | Dark | Light |
|---|---|---|
| Background | `#111214` | `#f4f1ec` |
| Surface | `#1c1e22` | `#faf8f5` |
| Surface 2 | `#24272d` | `#efece6` |
| Border | `#2e3138` | `#d6d0c6` |
| Border Hi | `#444952` | `#b8b0a4` |
| Text | `#d4d7dc` | `#2c2a26` |
| Text Muted | `#6b7280` | `#7a7568` |
| Text Dim | `#3d4149` | `#c4bfb5` |
| Accent | `#f59e0b` | `#c27b0a` |
| Accent Dim | `#b45309` | `#a06508` |
| OK | `#22c55e` | `#16a34a` |
| Error | `#ef4444` | `#dc2626` |

---

## Migration Complete

All five app-mode web apps now import `pipe-works-base.css` directly and share
identical design tokens, component classes, and font stacks. The Light Theme
Values table above represents the single source of truth for all projects.

| Project | PR | CSS Files | Approach |
|---|---|---|---|
| Axis Descriptor Lab | [#37](https://github.com/pipe-works/pipeworks_axis_descriptor_lab/pull/37) | `styles.css` (app-specific) | Removed ~650 duplicate lines |
| Name Generator | [#86](https://github.com/pipe-works/pipeworks_name_generation/pull/86) | `app.css` (app-specific) | Removed ~290 duplicate lines |
| Syllable Walk Web | — | `app.css` (app-specific) | Born migrated; built on `pipe-works-base.css` from inception |
| MUD Server Admin | [#132](https://github.com/pipe-works/pipeworks_mud_server/pull/132) | `admin.css` (consolidated) | Deleted 6 files, rewrote 1 |
| Image Generator | — | `app.css` (app-specific) | Born migrated; built on `pipe-works-base.css` from inception. Zero custom properties. |
