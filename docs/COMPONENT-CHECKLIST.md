# Component checklist

Build all of these for every project, unless the brief explicitly excludes them. The intent column tells you *what the component is for* — that should drive your design choices, not the catalog name.

The order below is the build order. Each section depends on the one above.

---

## Foundation (Part I) — token specimens, ~4 pages

| File                | Component         | Intent |
|---------------------|-------------------|--------|
| `01-palette.html`   | Palette           | Show paper, ink, accent, semantic, state. Frontispiece is the ink-on-paper proof. |
| `02-type.html`      | Type              | Three families with roles (display / chrome / record). Tracking ladder. One composed paragraph proving they coexist. |
| `03-geometry.html`  | Spacing & geometry | 4-px ruler, radius lineup, edge taxonomy, density specimen. |
| `04-motion.html`    | Motion            | Three named curves, four durations, one live demo. Reduced-motion honoured. |

## Primitives (Part II) — ~5 pages

| File                | Component             | Intent |
|---------------------|-----------------------|--------|
| `10-buttons.html`   | Buttons               | Three weights + one ornament for irreversible. **Render in scenes** (modal foot, list row, toolbar, split, hold-to-confirm). State grid only at the very end, small. |
| `11-inputs.html`    | Inputs                | The line-field default. Domain-specific *first* (vitals, dosage, ICD-10 for clinical; price, ticker for finance; etc.). Generic last. |
| `12-selection.html` | Selection             | Checkbox, radio, switch, chips, combobox, room/bed-style picker. The "selection is a tick, not a fill" stance. |
| `13-datetime.html`  | Date & time           | Calendar, clock, recurrence-as-sentence, DOB-with-auto-age. Domain shapes which to emphasize. |
| `14-specialized.html` | Specialized inputs  | Drop zone, signature pad, body diagram (or domain equivalent), SOAP / structured notes (or equivalent), PIN, DICOM thumb (or domain media). |

## Data & state (Part III) — ~10 pages

| File                       | Component               | Intent |
|----------------------------|-------------------------|--------|
| `20-tables.html`           | Tables                  | Worklist with filters, selection bar, expandable rows, density. |
| `21-<domain>.html`         | The domain's signature data display | Lab specimen for clinical; order book for trading; product card for ecommerce; etc. **The single most-designed page.** |
| `22-<time-axis>.html`      | Time-axis specimen      | Vitals strip + MAR for clinical; P&L curve for finance; activity stream for productivity. |
| `23-charts.html`           | Charts                  | Bar, gantt, heatmap, donut, sparkline, funnel. Hairline-only by default. |
| `24-progress.html`         | Progress                | Linear, ring, stepper, indeterminate, plus a domain-specific gauge (IV drip, escrow, fundraising). |
| `25-skeletons-empty.html`  | Skeletons & empty       | Loading skeletons that mirror layout. Empty states in serif italic. Error with arterial-red leading edge. |
| `26-avatars-pills.html`    | Avatars · pills · status | Round for users-as-people, square for staff-as-badges. The full status taxonomy of the domain. |
| `27-cards.html`            | Cards                   | The signature card in three sizes. Staff/user profile. Equipment/product card. Stat tile. |
| `28-tooltips.html`         | Tooltips · popovers · hovercards | Tooltip chip, popover sheet, hovercards (4 species: user, staff, item, location). |
| `29-navigation.html`       | Navigation · shell · ⌘K · drawers | Top bar, left rail, command palette, drawer. The way the user moves through the system. |

## Surfaces (Part IV) — at least 3 fully-designed scenes

These are **the scenes that prove the system**. For Medcord they were patient banner / bed board / EMR / telehealth / equipment / staff / registration. For your project, ask: *"what are the three things this product does that nothing else does?"*

Each surface is a **complete situation**, not a component catalog. Real names. Real numbers. Real time-stamps. Real critical moments. The user should be able to imagine the operator using this surface, with their own hands, at the moment described.

Number them `30-`, `31-`, `32-`, etc.

## Overlays & system (Part V) — ~4 pages

| File                | Component                 | Intent |
|---------------------|---------------------------|--------|
| `40-modals.html`    | Modals                    | Confirm, form, irreversible (with hold-to-confirm or typed-confirm), critical override, two-person verification, session-timeout. **The CRITICAL modal is mandatory** — every system has one. |
| `41-feedback.html`  | Toasts · banners · alerts | Toast slips, page-rule banners, callouts, undo strips, optimistic indicators, context menus. |
| `42-cross.html`     | Cross-record patterns     | Mention chips, approval cards, sharing, permissions matrix, audit log, attachment chips, saved views, bulk-action bar, AI assist (suggestions only — never auto-actions), sensitivity ribbon. |
| `43-icons.html`     | Iconography               | Sizes, the domain's specific glyphs hand-drawn into the UI grid, line vs filled rules. |

---

## How to deviate

If the brief is small, drop sections — but do **not** drop the surfaces. A system without scenes is a Bootstrap clone.

If the brief is large (a multi-vertical SaaS like Medcord), add more surfaces — one per vertical. The numbering stays in `30-`. Surfaces 31, 32, 33, 34, 35, 36 in Medcord.

If the brief has no clinical-style critical moments (e.g. a journaling app), the modal page can drop "two-person verification" but **must keep** "destructive confirm" — every system needs a way to say "are you sure?"

---

## What to skip without asking

- "Two-person verification" — only relevant for clinical, financial high-stakes, or compliance-heavy systems
- "DICOM viewer" — clinical only
- "Body diagram" — clinical only
- "MAR / time-axis" — depends on whether the product has scheduled events
- "AI assist chips" — only if the product has AI features

If you're not sure whether to skip, lean toward including. It's easier to delete than to add.

---

## What never to skip

- Foundation (palette, type, geometry, motion)
- Buttons in scenes
- The signature data display
- At least three surfaces
- Modals (with at least one irreversible variant)
- Iconography
- Empty / loading / error triad somewhere
