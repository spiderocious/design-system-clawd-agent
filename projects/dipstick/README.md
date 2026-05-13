# Dipstick

A digital station logbook for Nigerian filling-station owners with one to ten branches. Manager logs each day; owner sees the roll-up across branches. No hardware, no POS integration — just the cashier's exercise-book made shared, signed, and auditable.

**Stance:** Ledger broadsheet (catalog #2, money-serious). Warm cream paper, deep emerald accent, hairlines instead of shadows, Source Serif 4 + Inter + IBM Plex Mono. Numbers are the loudest object on the page.

**Brief:** "A simple product that enables filling station owners to manage it properly. They can own multiple branches, they can manage each branch. Nigerian context."

## Decisions

- **No hardware, no POS.** The system trusts the manager's entries. Discipline comes from posting / audit / void mechanics, not real-time telemetry.
- **Naira and litres are tabular monospace** at every size. The product reads like a ledger column, not a dashboard.
- **Money green, not Bootstrap green.** `#0E5C3A` deep emerald. Reserved for posted/balanced/confirmed and the brand mark — never decoration.
- **Shortage red is oxblood**, not Bootstrap red. `#9A1F18`. Reserved for shortages and voids.
- **PMS / AGO / DPK** are tiny inline marks — not chromatic billing. Product distinction is a quiet typographic dot.
- **Three signature scenes:** shift close, owner roll-up, tanker delivery. Plus branch day-book, price change, staff & shifts, expenses ledger.
- **CRITICAL idiom:** voiding a posted shift requires typing the literal word `VOID`. The only place we use a hazard stripe.

## File map

```
projects/dipstick/
├── index.html              ← gallery shell (sidebar + iframe)
├── thumb.html               ← gallery preview (reconciliation row)
├── _variations.html         ← Act III variations (A locked)
├── README.md
└── preview/
    ├── _foundation.css      ← tokens (paper, ink, emerald, type)
    ├── 00-welcome.html
    ├── 01-palette.html
    ├── 02-type.html
    ├── 03-geometry.html
    ├── 04-motion.html
    ├── 05-icons.html
    ├── 10-buttons.html
    ├── 11-inputs.html        ← litres, naira, meter, dip
    ├── 12-selection.html
    ├── 13-datetime.html      ← calendar with shift bar
    ├── 14-specialized.html   ← dipstick input, pump picker
    ├── 20-tables.html
    ├── 21-reconciliation.html ← ★ signature row
    ├── 22-tank.html
    ├── 23-charts.html
    ├── 24-progress.html
    ├── 25-skeletons-empty.html
    ├── 26-avatars-pills.html
    ├── 27-cards.html         ← branch summary card
    ├── 28-tooltips.html
    ├── 29-navigation.html    ← app shell + ⌘K
    ├── 30-shift-close.html    ← ★ scene
    ├── 31-rollup.html         ← ★ scene
    ├── 32-tanker.html         ← ★ scene
    ├── 33-daybook.html
    ├── 34-price-change.html
    ├── 35-staff.html
    ├── 36-expenses.html
    ├── 40-modals.html         ← incl. CRITICAL void
    ├── 41-feedback.html
    └── 42-cross.html          ← audit log + threads
```
