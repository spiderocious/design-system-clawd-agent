# Medcord Design System

## Company Overview

**Medcord** (codenamed "Caelum" for the platform) is an enterprise hospital management SaaS platform. Hospitals subscribe as tenants and use Medcord to run their entire operation across five core verticals:

1. **Patient Management** — registration, card issuance, check-in/check-out, triage, bed board, admission/discharge/transfer
2. **Employee/Staff Management** — shifts, schedules, credentials, PTO, time-clock, on-call
3. **Online Consultation & Assignments** — telehealth calls, provider assignment, consult queues, e-prescriptions
4. **Medical Records (EMR)** — full chart: vitals, medications, labs, imaging, notes, orders, problems, allergies, immunizations, documents, audit logs
5. **Equipment & Asset Management** — asset tracking, maintenance schedules, calibration records, consumables, sterilization

**Sources provided:** No external codebase or Figma was provided. This design system was constructed from first principles aligned with the product description above.

---

## Design Philosophy

**Aesthetic:** Clinical-modern, calm, trustworthy, information-dense without being noisy. Epic + Cerner reimagined by Linear + Stripe. Serious enough that doctors and nurses trust it; modern enough that they don't hate using it.

**Core Principles:**
- Information density without visual noise — clinicians scan, they don't browse
- Clarity over cleverness — never sacrifice legibility for style
- Semantic color carries meaning ALWAYS, decoration NEVER
- Critical information is unmistakable: allergies, drug interactions, abnormal vitals
- Calm by default, alarming only when warranted — alert fatigue is a real harm
- Accessibility is non-negotiable: WCAG AA minimum, tap targets ≥44px, focus rings always visible

---

## Content Fundamentals

**Tone:** Professional, clinical, direct. Never casual or playful. Never vague.

**Voice:**
- Second-person when addressing users: "Your schedule for today" not "User schedule"
- Third-person for patients, always: "Patient has 2 active allergies"
- Imperative for actions: "Admit", "Discharge", "Override", "Sign"
- Avoid passive voice in UI labels; prefer active
- Never use medical abbreviations without tooltip expansion on first use

**Casing:**
- UI labels: Title Case for section headers, sentence case for helper text
- Buttons: Sentence case (not ALL CAPS)
- Status pills: ALL CAPS for critical statuses (STAT, DNR, NPO), title case for workflow statuses
- MRNs, IDs, codes: always monospace, always uppercase

**Numbers:**
- Tabular figures for all clinical numerics
- Lab values: always include units and reference range
- Dates: MMM D, YYYY (May 1, 2026) in display; YYYY-MM-DD in export
- Times: 24h for clinical contexts, 12h for scheduling

**Emoji:** Never. Clinical contexts demand restraint.

**Examples of copy:**
- ✓ "2 active allergies — review before prescribing"
- ✗ "You have some allergies! 🚨"
- ✓ "Discharge requires attending physician sign-off"
- ✗ "Please make sure a doctor approves this!"
- ✓ "BP 142/88 — above normal range"
- ✗ "Blood pressure looks a little high"

---

## Visual Foundations

**Colors:**
- Neutral scale: 12-step cool-leaning gray from canvas white (#F8FAFB) to near-black (#0E1117)
- Primary brand: 9-shade deep teal (#0A4F6E → #E0F2F7) — confident, clinical, not sterile
- Module accents: Blue (Patient), Violet (Staff), Teal (Consultation), Forest Green (Records), Bronze (Equipment)
- Semantic: success/warning/danger/info — each with bg/border/fg variants
- Clinical-specific: Critical red, Abnormal-high amber, Abnormal-low purple, Normal green, Pending gray
- Allergy bands: red (allergy), orange (precaution), yellow (advisory)
- 8-color data-viz palette tuned for accessibility

**Typography:**
- UI: Geist Sans (Google Fonts: Inter as fallback) — weights 400/500/600/700
- Mono: JetBrains Mono — MRNs, lab IDs, dosages, timestamps, ICD-10 codes
- Tabular figures (`font-variant-numeric: tabular-nums`) everywhere numerics appear
- Scale: Display 2xl→xs, Heading 1–6, Body lg/md/sm/xs, Label, Caption, Overline, Code, Vitals-numeric

**Backgrounds:**
- Light theme: #F8FAFB canvas, #FFFFFF raised surfaces, #F1F5F8 sunken
- Dark theme: #0E1117 canvas, #161B22 raised, #0A0E13 sunken
- No full-bleed photography. No illustrations. No gradients on UI surfaces.
- Section dividers: 1px border, never heavy bands

**Spacing:** 4px base grid. Scale: 0, 4, 8, 12, 16, 20, 24, 32, 40, 48, 64, 80, 96

**Corner Radii:** 0, 4, 6, 8, 12, 16, 9999 (full). Cards: 8px. Buttons: 6px. Badges: 4px. Pills: full.

**Elevation:**
- Level 0: flat (borders only)
- Level 1: `0 1px 2px rgba(0,0,0,0.06)` — cards
- Level 2: `0 2px 8px rgba(0,0,0,0.08)` — dropdowns
- Level 3: `0 8px 24px rgba(0,0,0,0.10)` — modals
- Level 4: `0 16px 48px rgba(0,0,0,0.14)` — drawers
- Level 5: `0 24px 64px rgba(0,0,0,0.18)` — critical alerts
- No colored shadows. No thick drop shadows.

**Animation:**
- Ease-in: cubic-bezier(0.4,0,1,1) — exits
- Ease-out: cubic-bezier(0,0,0.2,1) — entrances
- Ease-in-out: cubic-bezier(0.4,0,0.2,1) — in-place
- Spring: for confirmation states only (very subtle)
- Durations: instant 0ms, fast 100ms, normal 200ms, slow 350ms
- No bounce. No playful spring. Clinical contexts demand calm.

**Hover states:** Subtle background fill change (neutral-100 over neutral-50). Never opacity changes for interactive elements.
**Active/press states:** Slightly darker fill. 1px inset border for buttons.
**Focus rings:** 2px offset, #0EA5E9 color. Always visible. Never hidden.
**Disabled states:** 40% opacity. Never pointer-events active.
**Read-only states (common in EMR):** Slightly sunken background, no border, no hover effect — visually distinct from disabled.

**Cards:**
- Light: white background, 1px `border: #E2E8F0`, 8px radius, level-1 shadow
- Dark: #161B22 background, 1px `border: #21262D`, 8px radius, level-1 shadow
- Interactive cards: hover adds level-2 shadow and border-color shift

**Imagery:** Placeholder only. No stock photography. DICOM uses grayscale gradients.

**Borders:**
- Subtle: 1px #F1F5F8 (light) / #1E2530 (dark) — between list items
- Default: 1px #E2E8F0 (light) / #21262D (dark) — card borders
- Strong: 1px #94A3B8 (light) / #475569 (dark) — inputs, emphasized
- Focus ring: 2px #0EA5E9 — focused inputs
- Critical ring: 2px #DC2626 — emergency contexts

---

## Iconography

**Approach:** Line icons, 1.5px stroke weight, 24px base size with 16/20/32 variants. No icon fonts. SVG inline or sprite.

**Sources:** No icon codebase provided. Lucide icons (CDN: unpkg.com/lucide) used as primary source — closest match to clinical needs. Healthcare-specific icons (stethoscope, syringe, pill, IV bag, etc.) are drawn as geometric SVGs or sourced from Lucide's healthcare subset.

**Usage rules:**
- 16px: dense table cell decorations, inline text icons
- 20px: standard UI (buttons, nav items, list rows)
- 24px: section headers, empty states
- 32px: hero/feature icons in empty states

**Color:** Icons inherit `currentColor`. Never hardcoded colors except for semantic states.

**Filled vs line:** Line for neutral/informational. Filled for selected/active/critical states.

---

## File Index

```
README.md                   ← This file
SKILL.md                    ← Agent skill manifest
colors_and_type.css         ← All CSS design tokens

assets/                     ← Logos and visual assets
  medcord-logo.svg          ← Primary wordmark

preview/                    ← Design system card files (shown in Design System tab)
  colors-neutral.html
  colors-brand.html
  colors-module-accents.html
  colors-semantic.html
  colors-clinical.html
  colors-status.html
  colors-dataviz.html
  typography-scale.html
  spacing-tokens.html
  radius-elevation.html
  motion-tokens.html
  iconography.html
  density-tokens.html
  buttons.html
  form-inputs.html
  selection-controls.html
  date-time.html
  specialized-inputs.html
  avatars.html
  badges-pills.html
  tooltips-popovers.html
  cards.html
  lists-tables.html
  lab-results-table.html
  stats-metrics.html
  charts.html
  progress.html
  skeletons.html
  empty-states.html
  navigation-shell.html
  drawers-panels.html
  feedback-overlays.html
  modals.html
  patient-mgmt.html
  staff-mgmt.html
  consultation.html
  emr.html
  equipment.html
  cross-module.html

ui_kits/
  medcord/
    README.md
    index.html
    Shell.jsx
    PatientBanner.jsx
    Navigation.jsx
    Charts.jsx
```

---

## Module Color Map

| Module | Accent Color | Hex |
|--------|-------------|-----|
| Patient Management | Deep Blue | #1D4ED8 |
| Staff/Employee | Violet | #7C3AED |
| Consultation | Teal | #0D9488 |
| Medical Records | Forest Green | #16A34A |
| Equipment/Assets | Warm Bronze | #B45309 |
