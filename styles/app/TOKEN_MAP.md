# Token Map — Variable Name Mapping

Cross-reference of CSS custom property names across all Pipe-Works app-mode projects.

> The website (editorial) uses a completely separate token system (`--ink-*`, `--paper-*`)
> and is not included here. See [`../editorial/STYLE_GUIDE.md`](../editorial/STYLE_GUIDE.md).

---

## Colour Tokens

| Base CSS (canonical) | Axis Descriptor Lab | Name Generator | MUD Server Admin |
|---|---|---|---|
| `--col-bg` | `--col-bg` | `--bg` | `--color-bg` |
| `--col-surface` | `--col-surface` | `--bg-soft` / `--panel` | `--color-surface` |
| `--col-surface-2` | `--col-surface-2` | `--panel-2` | `--color-surface-raised` |
| `--col-border` | `--col-border` | `--border` | `--color-border` |
| `--col-border-hi` | `--col-border-hi` | `--border-hi` | — (not defined) |
| `--col-text` | `--col-text` | `--text` | `--color-text` |
| `--col-text-muted` | `--col-text-muted` | `--muted` | `--color-muted` |
| `--col-text-dim` | `--col-text-dim` | `--text-dim` | — |
| `--col-accent` | `--col-accent` | `--accent` | `--color-accent` |
| `--col-accent-dim` | `--col-accent-dim` | `--accent-2` | — |
| `--col-accent-glow` | `--col-accent-glow` | `--accent-glow` | — |
| `--col-ok` | `--col-ok` | `--ok` | `--color-success` |
| `--col-err` | `--col-err` | `--err` | `--color-danger` |
| `--col-warn` | `--col-warn` | — | — |
| `--col-info` | `--col-info` | — | — |
| `--col-code-bg` | — (hardcoded `#0d0f12`) | `--code-bg` | — |
| `--col-code-text` | — (hardcoded) | `--code-text` | — |
| `--col-code-inline` | — | `--code-inline-text` | — |
| `--col-button-text` | — (hardcoded `#111`) | `--button-text` | — (hardcoded `#fff`) |
| `--col-backdrop` | — (hardcoded) | — (hardcoded) | — |
| `--col-tooltip-bg` | `--tooltip-bg` | — | — |
| `--col-tooltip-text` | `--tooltip-text` | — | — |
| `--col-tooltip-border` | `--tooltip-border` | — | — |
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
| `--font-mono` | `--font-mono` | `--font-mono` | — (not defined) |
| `--font-ui` | `--font-ui` | `--font-ui` | — (uses `"Sora"` directly on `:root`) |
| `--font-masthead` | — | — | — |
| `--font-headline` | — | — | — |
| `--font-body` | — | — | — |
| `--font-record` | — | — | — |
| `--font-symbols` | — | — | — |
| `--font-accent` | — | — | — |

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
| `--text-xs` (`0.70rem`) | `--text-xs` | — (hardcoded) | — (hardcoded various) |
| `--text-sm` (`0.80rem`) | `--text-sm` | — (hardcoded) | — |
| `--text-base` (`0.875rem`) | `--text-base` | — (hardcoded) | — (`16px` on `:root`) |
| `--text-lg` (`1.0rem`) | `--text-lg` | — (hardcoded) | — |
| `--text-xl` (`1.15rem`) | `--text-xl` | — (hardcoded) | — |

---

## Spacing Tokens

| Base CSS (canonical) | Axis Descriptor Lab | Name Generator | MUD Server Admin |
|---|---|---|---|
| `--sp-1` (`0.25rem`) | `--sp-1` | — (hardcoded) | — (hardcoded) |
| `--sp-2` (`0.5rem`) | `--sp-2` | — (hardcoded) | — (hardcoded) |
| `--sp-3` (`0.75rem`) | `--sp-3` | — (hardcoded) | — (hardcoded) |
| `--sp-4` (`1rem`) | `--sp-4` | — (hardcoded) | — (hardcoded) |
| `--sp-6` (`1.5rem`) | `--sp-6` | — (hardcoded) | — (hardcoded) |

---

## Layout Tokens

| Base CSS (canonical) | Axis Descriptor Lab | Name Generator | MUD Server Admin |
|---|---|---|---|
| `--header-h` (`2.75rem`) | `--header-h` | `--header-h` | — (no fixed header) |
| `--statusbar-h` (`1.75rem`) | `--statusbar-h` | `--statusbar-h` | — (no status bar) |
| `--panel-pad` (`1rem`) | `--panel-pad` | — | — |
| `--radius-sm` (`4px`) | — (hardcoded) | — (hardcoded) | — (uses `10px`) |
| `--radius-md` (`8px`) | — (hardcoded) | — (hardcoded) | — (uses `12-16px`) |
| `--radius-lg` (`12px`) | — (hardcoded) | — (hardcoded) | — (uses `18-20px`) |
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
| `--transition-fast` (`100ms ease`) | `--transition-fast` | — (hardcoded) | — (hardcoded `0.15s ease`) |
| `--transition-med` (`200ms ease`) | `--transition-med` | — (hardcoded) | — (hardcoded `0.2s ease`) |

---

## Component Class Mapping

| Base CSS | Axis Descriptor Lab | Name Generator | MUD Server Admin |
|---|---|---|---|
| `.btn` | `.btn` | `button` (raw) | — (no button class system) |
| `.btn--primary` | `.btn--primary` | `button` (default style) | `.form button`, `.detail-form button` |
| `.btn--secondary` | `.btn--secondary` | — | `.actions button`, `.character-actions button` |
| `.btn--ghost` | `.btn--ghost` | `.theme-toggle` | `.theme-toggle`, `.logout` |
| `.btn--sm` | `.btn--sm` | — | — |
| `.btn--icon` | — | `.icon-btn` | — |
| `.input` | `.input` | `input` (raw) | `.form input`, `.detail-form input` |
| `.select` | `.select` | `select` (raw) | `.detail-form select` |
| `.code-editor` | `.code-editor` | — | — |
| `.badge` | `.badge` | — | `.status-pill` |
| `.badge--active` | `.badge--active` | — | `.status-pill.is-online` |
| `.card` | — | `.db-card`, `.favorites-card` | `.card`, `.detail-card`, `.kpi-card` |
| `.modal` | — | `.modal` | — |
| `.modal__backdrop` | — | `.modal-backdrop` | — |
| `.modal__card` | — | `.modal-card` | — |
| `.spinner` | `.spinner` | — | — |
| `.divider` | `.divider` | `.section-divider` | — |
| `.hidden` | `.hidden` | — | — |
| `.u-sr-only` | — | — | — |
| — | — | — | `.tag` (pill-shaped chip) |
| — | — | — | `.toast`, `.toast-container` |
| — | — | `.tab`, `.tab.active` | `.tab-button`, `.tab-button.is-active` |

---

## Light Theme Values

Axis Descriptor Lab and Name Generator share identical palettes.
The MUD Server Admin uses a completely different palette (see Colour Value
Differences above).

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
