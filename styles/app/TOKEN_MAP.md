# Token Map — Variable Name Mapping

Cross-reference of CSS custom property names across all Pipe-Works app-mode projects.

> The website (editorial) uses a completely separate token system (`--ink-*`, `--paper-*`)
> and is not included here. See [`../editorial/STYLE_GUIDE.md`](../editorial/STYLE_GUIDE.md).

### Migration Status

| Project | Status | Notes |
|---|---|---|
| Axis Descriptor Lab | **Migrated** | Imports `pipe-works-base.css` directly. All tokens canonical. |
| Name Generator | **Migrated** | Imports `pipe-works-base.css` directly. All tokens canonical. |
| MUD Server Admin | Not started | Full aesthetic alignment needed. |

---

## Colour Tokens

| Base CSS (canonical) | Axis Descriptor Lab | Name Generator | MUD Server Admin |
|---|---|---|---|
| `--col-bg` | `--col-bg` | `--col-bg` | `--color-bg` |
| `--col-surface` | `--col-surface` | `--col-surface` | `--color-surface` |
| `--col-surface-2` | `--col-surface-2` | `--col-surface-2` | `--color-surface-raised` |
| `--col-border` | `--col-border` | `--col-border` | `--color-border` |
| `--col-border-hi` | `--col-border-hi` | `--col-border-hi` | — (not defined) |
| `--col-text` | `--col-text` | `--col-text` | `--color-text` |
| `--col-text-muted` | `--col-text-muted` | `--col-text-muted` | `--color-muted` |
| `--col-text-dim` | `--col-text-dim` | `--col-text-dim` | — |
| `--col-accent` | `--col-accent` | `--col-accent` | `--color-accent` |
| `--col-accent-dim` | `--col-accent-dim` | `--col-accent-dim` | — |
| `--col-accent-glow` | `--col-accent-glow` | `--col-accent-glow` | — |
| `--col-ok` | `--col-ok` | `--col-ok` | `--color-success` |
| `--col-err` | `--col-err` | `--col-err` | `--color-danger` |
| `--col-warn` | `--col-warn` | — | — |
| `--col-info` | `--col-info` | — | — |
| `--col-code-bg` | `--col-code-bg` | `--col-code-bg` | — |
| `--col-code-text` | `--col-code-text` | `--col-code-text` | — |
| `--col-code-inline` | `--col-code-inline` | `--col-code-inline` | — |
| `--col-button-text` | `--col-button-text` | `--col-button-text` | — (hardcoded `#fff`) |
| `--col-backdrop` | `--col-backdrop` | `--col-backdrop` | — |
| `--col-tooltip-bg` | `--col-tooltip-bg` | — | — |
| `--col-tooltip-text` | `--col-tooltip-text` | — | — |
| `--col-tooltip-border` | `--col-tooltip-border` | — | — |
| `--col-diff-add` | `--col-diff-add` | — | — |
| `--col-diff-del` | `--col-diff-del` | — | — |
| `--col-diff-add-text` | `--col-diff-add-text` | — | — |
| `--col-diff-del-text` | `--col-diff-del-text` | — | — |
| — | — | — | `--color-bg-alt` (no equivalent) |
| — | — | — | `--color-sidebar` (no equivalent) |
| — | — | — | `--shadow-soft` (no equivalent) |

### MUD Server Admin — Colour Value Differences

The admin shell currently uses a **completely different palette** from the app tools
standard. These values will need to change during alignment:

| Token | Admin Current (Light) | App Tools (Light) | Admin Current (Dark) | App Tools (Dark) |
|---|---|---|---|---|
| Background | `#e9edf4` (cool blue-grey) | `#f4f1ec` (warm paper) | `#0b111a` (navy) | `#111214` (neutral dark) |
| Surface | `#ffffff` (white) | `#faf8f5` (warm white) | `#1a2332` (blue-dark) | `#1c1e22` (neutral dark) |
| Accent | `#2563eb` (blue) | `#c27b0a` (amber) | `#6aa0ff` (light blue) | `#f59e0b` (amber) |
| OK/Success | `#1d7a3a` (green) | `#16a34a` (green) | `#6ad98f` | `#22c55e` |
| Error/Danger | `#c0392b` (red) | `#dc2626` (red) | `#ff6b6b` | `#ef4444` |

---

## Typography Tokens

| Base CSS (canonical) | Axis Descriptor Lab | Name Generator | MUD Server Admin |
|---|---|---|---|
| `--font-mono` | `--font-mono` | `--font-mono` (via base) | — (not defined) |
| `--font-ui` | `--font-ui` | `--font-ui` (via base) | — (uses `"Sora"` directly on `:root`) |
| `--font-heading` | `--font-heading` (via base) | `--font-heading` (via base) | — |
| `--font-body` | `--font-body` (via base) | `--font-body` (via base) | — |
| `--font-masthead` | `--font-masthead` (via base) | `--font-masthead` (via base) | — |
| `--font-headline` | `--font-headline` (via base) | `--font-headline` (via base) | — |
| `--font-record` | `--font-record` (via base) | `--font-record` (via base) | — |
| `--font-symbols` | `--font-symbols` (via base) | `--font-symbols` (via base) | — |
| `--font-accent` | `--font-accent` (via base) | `--font-accent` (via base) | — |

### MUD Server Admin — Typography Differences

The admin shell uses **no font tokens** and no monospace font:

| Aspect | Admin Current | App Tools Standard |
|---|---|---|
| Base font | `"Sora", "Avenir Next", "Segoe UI", sans-serif` | `system-ui, -apple-system, "Segoe UI", sans-serif` |
| Headings | Sans-serif (inherited) | Monospace (`--font-mono`) |
| Buttons | Sans-serif (inherited) | Monospace (`--font-mono`) |
| Inputs | Sans-serif (inherited) | Monospace (`--font-mono`) |
| Tables | Sans-serif (inherited) | Monospace (`--font-mono`) |
| Font size | `16px` base | `0.875rem` (14px) base |

---

## Type Scale Tokens

| Base CSS (canonical) | Axis Descriptor Lab | Name Generator | MUD Server Admin |
|---|---|---|---|
| `--text-xs` (`0.70rem`) | `--text-xs` | `--text-xs` (via base) | — (hardcoded various) |
| `--text-sm` (`0.80rem`) | `--text-sm` | `--text-sm` (via base) | — |
| `--text-base` (`0.875rem`) | `--text-base` | `--text-base` (via base) | — (`16px` on `:root`) |
| `--text-lg` (`1.0rem`) | `--text-lg` | `--text-lg` (via base) | — |
| `--text-xl` (`1.15rem`) | `--text-xl` | `--text-xl` (via base) | — |

---

## Spacing Tokens

| Base CSS (canonical) | Axis Descriptor Lab | Name Generator | MUD Server Admin |
|---|---|---|---|
| `--sp-1` (`0.25rem`) | `--sp-1` | `--sp-1` (via base) | — (hardcoded) |
| `--sp-2` (`0.5rem`) | `--sp-2` | `--sp-2` (via base) | — (hardcoded) |
| `--sp-3` (`0.75rem`) | `--sp-3` | `--sp-3` (via base) | — (hardcoded) |
| `--sp-4` (`1rem`) | `--sp-4` | `--sp-4` (via base) | — (hardcoded) |
| `--sp-6` (`1.5rem`) | `--sp-6` | `--sp-6` (via base) | — (hardcoded) |

---

## Layout Tokens

| Base CSS (canonical) | Axis Descriptor Lab | Name Generator | MUD Server Admin |
|---|---|---|---|
| `--header-h` (`2.75rem`) | `--header-h` | `--header-h` (via base) | — (no fixed header) |
| `--statusbar-h` (`1.75rem`) | `--statusbar-h` | `--statusbar-h` (via base) | — (no status bar) |
| `--panel-pad` (`1rem`) | `--panel-pad` | `--panel-pad` (via base) | — |
| `--radius-sm` (`4px`) | `--radius-sm` | `--radius-sm` (via base) | — (uses `10px`) |
| `--radius-md` (`8px`) | `--radius-md` | `--radius-md` (via base) | — (uses `12-16px`) |
| `--radius-lg` (`12px`) | `--radius-lg` | `--radius-lg` (via base) | — (uses `18-20px`) |
| — | — | — | `--layout-max` (`1600px`) |
| — | — | — | `--layout-pad` (`32px`) |

### MUD Server Admin — Layout Differences

| Aspect | Admin Current | App Tools Standard |
|---|---|---|
| Shell pattern | Sidebar (280px) + content | Header + status bar |
| Border radius | 10–20px (rounded, SaaS-style) | 4–12px (tight, industrial) |
| Card padding | 1.5–2.75rem (spacious) | 0.75–0.85rem (compact) |
| Max content width | `1600px` | None (fills container) |
| Default theme | Light | Dark |
| Theme toggle | `html[data-theme="dark"]` | `html[data-theme="light"]` |

---

## Animation Tokens

| Base CSS (canonical) | Axis Descriptor Lab | Name Generator | MUD Server Admin |
|---|---|---|---|
| `--transition-fast` (`100ms ease`) | `--transition-fast` | `--transition-fast` (via base) | — (hardcoded `0.15s ease`) |
| `--transition-med` (`200ms ease`) | `--transition-med` | `--transition-med` (via base) | — (hardcoded `0.2s ease`) |

---

## Component Class Mapping

| Base CSS | Axis Descriptor Lab | Name Generator | MUD Server Admin |
|---|---|---|---|
| `.btn` | `.btn` | `.btn` | — (no button class system) |
| `.btn--primary` | `.btn--primary` | `.btn--primary` | `.form button`, `.detail-form button` |
| `.btn--secondary` | `.btn--secondary` | `.btn--secondary` | `.actions button`, `.character-actions button` |
| `.btn--ghost` | `.btn--ghost` | — | `.theme-toggle`, `.logout` |
| `.btn--sm` | `.btn--sm` | `.btn--sm` | — |
| `.btn--icon` | — | `.btn--icon` | — |
| `.input` | `.input` | `.input` | `.form input`, `.detail-form input` |
| `.select` | `.select` | `.select` | `.detail-form select` |
| `.range-input` | — | `.range-input` | — |
| `.code-editor` | `.code-editor` | — | — |
| `.badge` | `.badge` | — | `.status-pill` |
| `.badge--active` | `.badge--active` | — | `.status-pill.is-online` |
| `.card` | — | `.card` (help entries) | `.card`, `.detail-card`, `.kpi-card` |
| `.modal` | — | `.modal` | — |
| `.modal__backdrop` | — | `.modal-backdrop` (hyphenated) | — |
| `.modal__card` | — | `.modal-card` (hyphenated) | — |
| `.spinner` | `.spinner` | — | — |
| `.divider` | `.divider` | `.divider` | — |
| `.hidden` | `.hidden` | — | — |
| `.u-sr-only` | `.u-sr-only` (via base) | — | — |
| — | — | — | `.tag` (pill-shaped chip) |
| — | — | — | `.toast`, `.toast-container` |
| — | — | `.tab`, `.tab.active` | `.tab-button`, `.tab-button.is-active` |

---

## Light Theme Values

Axis Descriptor Lab and Name Generator both import `pipe-works-base.css`
directly and share identical palettes via canonical tokens. The MUD Server
Admin uses a completely different palette (see Colour Value Differences above).

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

## MUD Server Admin — Alignment Summary

The admin shell requires the most significant migration of any app-mode project.
The full alignment plan is documented in `MIGRATION_NOTES.md`, section 3.

**High-level changes needed:**

1. **Token rename:** `--color-*` -> `--col-*` (prefix change)
2. **Palette swap:** Blue accent -> amber, cool greys -> warm greys
3. **Default theme flip:** Light -> dark (with light as toggle)
4. **Typography overhaul:** Drop "Sora", adopt monospace-dominant `--font-mono`
5. **Radius tightening:** 10–20px -> 4–12px
6. **Spacing compaction:** Reduce card/panel padding to match app tools density
7. **Layout reconsideration:** Sidebar layout may stay (appropriate for admin) but
   needs to use base CSS tokens and component classes
8. **Component class adoption:** Replace raw selectors with `.btn`, `.input`, `.card`, etc.
