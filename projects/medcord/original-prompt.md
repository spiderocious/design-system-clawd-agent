Build a comprehensive design system showcase for "Caelum" (rename if you have a stronger instinct — I want a name that works for a hospital management SaaS: clinical, trustworthy, modern, not cold). Caelum is a multi-tenant platform that hospitals sign up to and use to run their entire operation: patient management (registration, card issuance, check-in/check-out), employee management (shifts, schedules, credentials), online consultation and assignments, electronic medical records (EMR) per patient, and equipment/asset management.

This is NOT a working app. NOT pages. NOT flows. NOT product screens.
This is a STATIC DESIGN SYSTEM CANVAS — like a Storybook + Figma component library page. Every primitive, every state, every variant, every domain-specific composed component, laid out on one long scrollable canvas with a sticky section nav.

Treat this as the inventory a senior design systems team at a serious health-tech company would document before greenlighting product teams to build. Default to MORE, not less. If you wonder whether to include a variant, include it. Push past the obvious. Healthcare UI lives or dies on edge-case states (allergies, contraindications, critical values, missing data) — surface them.

═══════════════════════════════════════════════
DESIGN PHILOSOPHY (LOCK THIS IN)
═══════════════════════════════════════════════

Aesthetic: clinical-modern, calm, trustworthy, information-dense without being noisy. Think Epic and Cerner reimagined by Linear and Stripe. Serious enough that doctors and nurses trust it; modern enough that they don't hate using it.

Principles:
- Information density without visual noise — clinicians scan, they don't browse
- Clarity over cleverness — never sacrifice legibility for style
- Semantic color carries meaning ALWAYS, decoration NEVER
- Critical information is unmistakable: allergies, drug interactions, abnormal vitals must be impossible to miss
- Calm by default, alarming only when warranted — alert fatigue is a real harm
- Accessibility is non-negotiable: WCAG AA contrast minimum, tap targets ≥44px, focus rings always visible
- Consistency across all 5 verticals — a button in Patient Mgmt looks identical to a button in Asset Mgmt

Typography:
- UI: Inter, Geist, or a similar humanist sans — full weight scale 400/500/600/700
- Display: same family, tighter tracking at large sizes
- Mono: JetBrains Mono — for medical record numbers (MRNs), lab IDs, dosages, timestamps, codes (ICD-10, CPT)
- Tabular figures EVERYWHERE numerics matter (vitals, labs, dosages, dates, IDs)

═══════════════════════════════════════════════
PART 1 — DESIGN TOKENS
═══════════════════════════════════════════════

Show as visual swatches, specimens, and rulers — NOT as code. Every token visible in light AND dark theme side by side.

1.1 Color tokens
- Neutral scale: 12 steps from canvas-white to ink-black, slight cool/clinical lean
- Primary brand accent: 9 shades (50–900) — a confident teal or deep blue (clinical without being sterile)
- Per-module accent palette — one distinct accent per vertical, harmonized:
  · Patient Mgmt (deep blue)
  · Staff/Employee (violet)
  · Consultation (teal)
  · Medical Records (forest green)
  · Assets/Equipment (warm bronze)
  Show each as a 5-shade ramp.
- Semantic: success, warning, danger, info, neutral — each with bg/border/fg variants for badges/banners
- CLINICAL semantic colors (this is critical, separate from generic semantic):
  · Critical / code red — high-saturation red for life-threatening alerts only
  · Abnormal-high — amber/red for out-of-range labs above
  · Abnormal-low — purple/blue for out-of-range labs below
  · Normal / within range — muted green
  · Pending / awaiting — neutral gray with subtle pulse
  · STAT / urgent — distinct from generic warning
- Status colors specific to healthcare workflow: scheduled, checked-in, in-triage, in-room, with-provider, awaiting-labs, awaiting-discharge, discharged, no-show, cancelled, admitted, transferred
- Allergy/alert colors: red-band for allergy, orange-band for precaution, yellow-band for advisory
- Data-viz palette: 8 categorical colors that work in vitals charts and lab trends without clashing
- Surface tokens: canvas, raised, sunken, overlay, scrim
- Border tokens: subtle, default, strong, focus-ring, critical-ring (for emergency contexts)

1.2 Typography scale
Display 2xl → xs, Heading 1–6, Body lg/md/sm/xs, Label, Caption, Overline, Code/Mono, Vitals-numeric (large tabular for displaying vital signs)
For each: sample text, font, size, weight, line-height, letter-spacing, use case

1.3 Spacing scale (4px base, 0–96px) as visual ruler
1.4 Radius scale (0, 4, 6, 8, 12, 16, full) on rectangles
1.5 Elevation scale (0–5) on cards, both themes
1.6 Iconography spec: 16/20/24/32 sizes, line + filled variants, sample 40+ healthcare-aware icon set drawn (stethoscope, syringe, pill, IV bag, heart, lungs, brain, bed, wheelchair, gurney, microscope, lab vial, scalpel, bandage, plus general UI icons)
1.7 Motion tokens: ease-in, ease-out, ease-in-out, spring + duration tokens (instant/fast/normal/slow). NO bouncy or playful motion — clinical contexts demand calm.
1.8 Z-index scale (named layers: base, dropdown, sticky, modal, toast, tooltip, critical-alert)
1.9 Breakpoints (mobile/tablet/desktop/wide — including a wall-mounted-display breakpoint for nurses' stations)
1.10 Density tokens: compact / default / comfortable — show same patient list at each density

═══════════════════════════════════════════════
PART 2 — PRIMITIVES (every state, every variant)
═══════════════════════════════════════════════

For each: default, hover, focus-visible, active, disabled, loading, error, success, read-only — light AND dark, sm/md/lg where applicable.

2.1 Buttons
Primary, secondary, tertiary/ghost, outline, destructive, destructive-ghost, success, CRITICAL (a special variant for irreversible clinical actions like "Discharge against medical advice" or "Override allergy warning")
+ Icon-only, icon-leading, icon-trailing, with badge count, with kbd shortcut hint
+ Split button, button group, segmented control, toggle button, FAB
+ Loading button (spinner replacing label), success state (checkmark momentarily)
+ Confirm-by-hold button (for destructive medical actions — show progress ring filling)

2.2 Form inputs
Text input — all states above
Textarea with auto-resize and char count (for clinical notes)
Search input with clear + loading
Password with show/hide
Number input with steppers
Currency input (for billing)
Email/URL with validation states
Input with prefix/suffix slots
Input group (joined inputs, e.g., systolic/diastolic BP)
Floating label vs static label vs no label
Read-only vs disabled (visually distinct — read-only common in EMR for signed records)
Inline validation with helper text
SPECIALIZED: vitals input (BP as 120/80), height (ft+in OR cm), weight (lb OR kg with unit toggle), temperature (°F/°C toggle), dosage (number + unit dropdown like mg/mL/IU)
ICD-10 / CPT code input with autocomplete dropdown showing code + description
Drug/medication search input with autocomplete showing generic + brand + strength

2.3 Selection
Checkbox: unchecked, checked, indeterminate, disabled, error, required
Checkbox group (vertical + horizontal)
Radio + radio group + radio cards (e.g., "Pain scale 0–10" as radio cards)
Switch: off/on/disabled, sm/md/lg
Toggle chips, filter chips, removable chips
Select / dropdown: simple, searchable, multi, grouped, with avatars, with descriptions, async-loading
Combobox / autocomplete (heavily used in EMR for diagnoses, medications, procedures)
Multi-value chip input (allergies, problem list, current medications)
Provider/staff picker (with role + specialty visible)
Department picker, Room picker, Bed picker

2.4 Date/time
Date picker (single, range)
Time picker (with seconds for medication timing)
Datetime picker
Timezone selector
Recurrence pattern builder (for medication schedules: "every 8 hours", "QID", "PRN")
Duration input
Date of birth picker (with age auto-calculated and shown adjacent)
Calendar picker variants: month, year, decade

2.5 Sliders & ranges
Single, range, with marks, with input, vertical
Pain scale slider (0–10 with face emojis at endpoints — use clinical Wong-Baker style restraint)

2.6 File handling
Drop zone (idle, hover-active, uploading, success, error)
File list item with progress, cancel, retry
DICOM image preview (X-ray, MRI thumbnail) — show as placeholder with grayscale gradient + "DICOM" label
Lab result PDF preview chip
Insurance card upload (front/back paired)
ID document upload (front/back paired)
Avatar/photo upload with circular crop

2.7 Specialized inputs
PIN / OTP input (for staff badge re-authentication on shared workstations)
Rating (stars + numeric for patient satisfaction)
Signature pad (large, prominent — for consent forms, discharge summaries)
Witness signature pad (paired with primary)
Body diagram selector (front/back human silhouette where clinician taps to mark injury/symptom location) — render this as an SVG with selectable regions
Markdown editor with toolbar (for clinical notes)
SOAP note structured input (Subjective / Objective / Assessment / Plan as labeled sections)

═══════════════════════════════════════════════
PART 3 — DATA DISPLAY
═══════════════════════════════════════════════

3.1 Avatars
Patient avatar (sm/md/lg/xl/2xl), with status dot, photo, initials, with patient-id-band
Staff avatar with role-ring color (MD/RN/Tech/Admin/Pharmacist), with on-shift indicator (green pulse) / off-shift (gray)
Squared avatars for departments / wards
Avatar group/stack with overflow count
Critical-patient ring (red outline) variant

3.2 Badges & pills
Count badges (dot, number, 99+)
Status pills with all healthcare workflow statuses listed in Part 1.1
Acuity level pills (ESI 1–5 for triage, with red→green gradient mapping severity)
Allergy band (red, ALWAYS visible on patient cards — non-dismissible)
Code status pill (Full Code, DNR, DNI, DNAR — with distinctive colors)
Isolation precaution pill (Contact, Droplet, Airborne, Neutropenic — color-coded)
Fall-risk pill, Aspiration-risk pill, NPO (nothing by mouth) pill
Insurance status pill (verified, pending, self-pay, denied)
Priority pills (STAT, ASAP, Routine)
Keyboard shortcut pills

3.3 Tooltips & popovers
Tooltip top/right/bottom/left, with arrow, with title+body, with kbd shortcut
Popover with form, with menu, with rich content, with footer actions
Hovercard variants: patient hovercard (mini summary: name, MRN, DOB, age, allergies band, code status, attending), staff hovercard (name, role, dept, pager, on-shift), medication hovercard (drug name, dose, route, frequency, last given, next due, indication), room/bed hovercard (occupant, status, isolation)

3.4 Cards
Basic, with header, with media, with footer actions, interactive/clickable, selected, draggable, compact, expanded, summary stat, comparison
Patient summary card (the central object — show this in multiple sizes/densities)
Staff profile card
Equipment card

3.5 Lists
Simple, with avatar + metadata, with trailing action, sortable/draggable
Patient list row (avatar, name, MRN, DOB+age, location/bed, attending, status, alerts strip)
Worklist row (compact dense version for nurses' stations)
Inset list (settings style)
With section headers, sticky group headers
Tree list (departments → wards → rooms → beds)

3.6 Tables (CRITICAL for healthcare — go very deep)
- Default with sort indicators
- Selectable rows (single + multi with header checkbox)
- Bulk action bar that appears on selection
- Resizable / reorderable / pinnable columns
- Column visibility toggle
- Filter row beneath header
- Row actions: hover-revealed icons, overflow menu
- Expandable rows with detail panel inline (e.g., expand a patient row to see vitals trend)
- Grouped rows with collapsible group headers (group by ward, by attending, by status)
- Sticky header, sticky first column
- Loading state (skeleton rows)
- Empty state inside table
- Error state inside table
- Pagination (numbered, prev/next, jump to page, page-size)
- Density toggle (compact for worklists, comfortable for review)
- Inline cell edit (click to edit)
- Cell types: text, number (right-aligned), currency, date, time, date+time, status pill, avatar+name, MRN, vitals value with abnormal-flag indicator, lab result with reference range and H/L flag, allergy chip list, action menu, sparkline (vitals trend)
- Critical row highlight (red left border for patients with critical values)
- Lab result table specifically: show value, unit, reference range, H/L/Critical flag, trend arrow, time of collection — render this as its own specimen

3.7 Trees & hierarchies
Department/ward/room/bed tree, org chart (medical staff), problem list with parent/child diagnoses

3.8 Stats & metrics
Big number with delta (+/-)
KPI tile with sparkline (e.g., "Avg LOS 4.2 days ↓ 0.3")
Comparison stat (vs prev period)
Goal progress (e.g., readmission rate vs target)
Gauge meter (e.g., bed occupancy %)
Census stat tile, ED-throughput tile, OR-utilization tile
Vitals stat group (HR / BP / RR / SpO2 / Temp displayed as 5-up tile with abnormal flagging)

3.9 Charts (drawn as SVG specimens, not real data)
Line, multi-line (vitals over 24h with reference bands shaded)
Vitals strip (HR + BP + SpO2 + Temp stacked sharing X-axis)
Lab trend line with reference range bands and H/L markers
Bar (vertical + horizontal), grouped, stacked
Donut, pie (use sparingly — only for true part-to-whole like patient demographics)
Sparkline
Heatmap (bed occupancy by hour-of-day × day-of-week)
Gantt bar (OR scheduling)
Timeline strip (medication administration record — MAR)
Funnel (referral → consult → procedure)
Each with: legend, axis labels, hover tooltip example, empty state, loading skeleton

3.10 Progress
Linear bar, circular ring, segmented/stepped, indeterminate (shimmer + dot bounce)
Triage progress (Registered → Triaged → Roomed → Seen → Disposition)
Discharge progress
IV drip progress (volume infused / total)

3.11 Skeletons
Text line, paragraph, avatar, card, list item, table row, chart, vitals strip, full page

3.12 Empty states
Per module: empty patient list, no appointments today, no active consultations, blank medical record, no equipment registered, no shifts scheduled, no incoming calls, no labs pending, no medications due
Each illustrated lightly + title + description + primary CTA

═══════════════════════════════════════════════
PART 4 — NAVIGATION & SHELL
═══════════════════════════════════════════════

4.1 Global app shell
- Top global bar: hospital/tenant switcher (logo + hospital name + dropdown, since this is multi-tenant SaaS), module launcher (5-tile grid for the 5 verticals), global patient search (prominent — clinicians search patients constantly, by name/MRN/DOB), notifications, help, profile menu with role indicator
- Acting-as-role indicator (a clinician might be in MD-mode vs admin-mode — make this explicit)
- Left primary nav: collapsed (icons) and expanded (icons + labels), with module accent color on active item
- Show the module launcher OPEN as a separate component showing all 5 module tiles + their icons

4.2 In-product navigation
Top app bar, breadcrumbs, tabs (underline, pill, vertical, with counts, with icons, scrollable)
Stepper/wizard (horizontal + vertical) — for patient registration, consultation flow, discharge flow
Pagination (all variants from table)
Command palette (⌘K) open with: recent patients, suggested actions, search results grouped by type (patients, staff, rooms, equipment, orders)
Quick-action speed dial (for mobile clinicians)

4.3 Drawers & panels
Right-edge patient detail drawer (with header, scrollable body, sticky footer actions like Admit/Discharge/Transfer)
Left-edge filter drawer
Bottom drawer (mobile)
Inline expanding row drawer
Multi-step drawer with breadcrumb (e.g., new-patient registration)

═══════════════════════════════════════════════
PART 5 — FEEDBACK & OVERLAYS
═══════════════════════════════════════════════

Toasts (info/success/warning/error/loading, with action, with undo, stacked, with progress)
Banners (page-level, dismissible, with CTA, persistent for system-wide notices like "EMR maintenance window 2am")
Alerts/callouts (subtle, prominent, with icon, with title+body)
CRITICAL ALERT MODAL — distinct, unmissable: drug allergy override, dosage out of range, duplicate order — must require explicit acknowledgement, not just dismissal
Modals: confirm (sm), form (md), wide (lg), full-screen (mobile), with sticky footer, with stepper header
Destructive-confirm with required-text-input ("type DISCHARGE to confirm")
Two-person verification modal (for high-risk medications — show two signature/auth fields)
Bottom sheets (mobile, snap points, handle)
Context menus (with sections, icons, kbd shortcuts, destructive item, submenus)
Inline confirmation, undo strip, optimistic-update indicator
Loading overlays (full-screen, contained, with progress text)
Empty/error/loading triad for every async surface
Session timeout warning modal (HIPAA — auto-logout warning with countdown)
Break-the-glass modal (emergency PHI access with reason required)

═══════════════════════════════════════════════
PART 6 — DOMAIN-SPECIFIC COMPOSED COMPONENTS
═══════════════════════════════════════════════

For each vertical, render the signature components. Use realistic clinical content — real-sounding patient names (diverse), real-sounding DOBs that produce reasonable ages, real-looking MRNs (8 digits), real-sounding diagnoses (use actual ICD-10 categories like "I10 Essential hypertension", "E11.9 Type 2 diabetes mellitus without complications"), real-looking medications (Lisinopril 10mg PO daily, Metformin 500mg PO BID), realistic vitals (BP 128/82, HR 76, SpO2 98%, Temp 98.6°F), realistic lab values with proper units (Hgb 13.2 g/dL, Na 138 mEq/L, Cr 0.9 mg/dL). NOT lorem ipsum.

6.1 PATIENT MANAGEMENT
- Patient banner (the persistent top-of-screen object when a patient chart is open): photo, full name, preferred name, DOB + age + sex, MRN, allergies-band (red, full-width if allergies exist), code status, isolation precautions, attending provider, location/bed, encounter type, encounter ID
- Patient registration mini-form card (demographics, contact, emergency contact, insurance, consent checklist)
- Patient ID card preview / issuance card (printable view: photo, name, DOB, MRN, barcode, hospital logo) — show both a "preview" version and an "issued" version with a watermark
- Card check-in scanner widget (barcode scan target, last scan timestamp, success/error states)
- Check-in queue row (arrival time, patient, appointment type, provider, wait time, triage acuity)
- Triage card (vitals snapshot, chief complaint, ESI level, time since arrival)
- Bed-board tile (room number, bed letter, occupant chip OR "available", isolation flag, housekeeping status: clean/dirty/in-progress)
- Admission form card, transfer form card, discharge summary card
- Discharge checklist (meds reconciled, follow-up scheduled, education provided, prescriptions sent, ride confirmed)
- No-show row, cancellation reason picker
- Insurance verification status row (payer, member ID, verified/pending/denied, copay)
- Consent form card (form name, signed/unsigned, witness signature status)

6.2 EMPLOYEE / STAFF MANAGEMENT
- Staff profile header (photo, name, credentials e.g. "MD, FACC", role, department, license # with expiry, NPI, specialty, hire date)
- Credential card (license type, number, issuer, issued date, expiry date, status: active/expiring-in-30/expired, upload verification doc)
- Shift tile (date, start, end, role, unit, status: scheduled/clocked-in/on-break/clocked-out/missed)
- Schedule grid cell (one cell per provider × day, showing shift block with color by role, on-call indicator, vacation/PTO marker)
- Shift swap request card (requester, date, replacement candidate list, status)
- Time-clock punch card (clock-in/clock-out buttons, current shift duration ticker, break button)
- On-call rotation card (who's on, contact method, escalation chain)
- Staff directory row (avatar, name, role, dept, pager, status dot)
- Department/unit overview tile (headcount, on-shift now, ratio: nurses-to-patients)
- PTO request card (type, dates, balance remaining, approver, status)

6.3 ONLINE CONSULTATION & ASSIGNMENTS
- Telehealth call frame (provider + patient tiles, mute/video/share controls, captions, recording indicator, network quality)
- Pre-visit waiting-room card (patient seen as "in waiting room", tech check status, intake form completion)
- Consultation queue row (patient, requested time, reason, assigned provider, status: waiting/in-progress/completed)
- Provider assignment card (drag patient to provider — show as draggable card with drop target)
- Auto-routing rule chip (e.g., "Cardiology requests → Dr. Patel queue")
- Consult request form (referring provider, reason, urgency, attachments)
- Asynchronous consult thread (message + image + reply pattern, with provider/patient distinction)
- E-prescription card (drug, sig, qty, refills, pharmacy, send button + sent state)
- Encounter wrap-up checklist (note signed, charges captured, orders sent, follow-up scheduled)
- Visit summary handoff card (for after-visit summary sent to patient)

6.4 MEDICAL RECORDS (EMR — go especially deep here)
- Chart navigation rail (vertical: Summary, Vitals, Meds, Labs, Imaging, Notes, Orders, Problems, Allergies, Immunizations, Procedures, Documents, Billing)
- Problem list row (diagnosis + ICD-10 code, status: active/resolved/chronic, onset date, last addressed)
- Medication list row (drug, strength, route, frequency, indication, prescriber, start date, last given, next due, status: active/held/discontinued)
- Medication administration record (MAR) cell (scheduled time, given/missed/held/refused, administrator initials, timestamp)
- Allergy entry (substance, reaction, severity: mild/moderate/severe/anaphylaxis, onset, source)
- Lab result row (test name, value, unit, reference range, flag: H/L/HH/LL/Critical, collected, resulted)
- Lab panel card (CBC, BMP, CMP, LFTs — show as grouped result block)
- Lab trend mini-chart (last 6 values with reference band)
- Imaging study row (modality, body region, ordered, performed, status: pending/in-progress/preliminary/final, radiologist)
- DICOM viewer placeholder card (image area + windowing controls + measurement tools — represented as labeled regions, not functional)
- Clinical note card (type: H&P, Progress, Discharge, Consult; author, signed status, addendum count)
- SOAP note rendered card (Subjective / Objective / Assessment / Plan sections clearly delimited)
- Order entry row (order type, details, priority, status: pending/active/completed/cancelled, ordering provider)
- Order set card (e.g., "Sepsis bundle" — checkbox list of grouped orders)
- Vital signs entry (BP, HR, RR, Temp, SpO2, Pain, Weight, Height — as a structured input grid with unit toggles)
- Growth chart card (pediatric — height/weight/HC percentile lines with patient marker)
- Immunization record row (vaccine, dose #, date, lot, administrator)
- Document repository row (filename, type, uploaded by, date, sensitivity flag)
- Audit log row (who accessed/modified what, when, from where) — privacy-critical, must be present
- Chart summary header (the at-a-glance: active problems, current meds, recent vitals, recent labs, allergies — as a compact dense overview tile)

6.5 EQUIPMENT & ASSET MANAGEMENT
- Asset card (thumbnail or icon, name, type, serial #, manufacturer, model, status: available/in-use/in-maintenance/out-of-service/retired, location, assigned-to)
- Asset detail header (large image, key facts strip, current location, assignment history)
- Maintenance schedule row (next service date, last service, technician, status, days-until)
- Calibration record row (date, performed-by, result: pass/fail, certificate)
- Assignment history row (department/staff, dates, condition note, returned-by)
- Bulk-import drop zone with mapping preview
- Consumable inventory row (item, qty on hand, par level, reorder point, supplier, expiry)
- Expiry alert chip (expiring in 30/14/7/expired)
- Sterilization cycle card (load #, contents, cycle type, indicator result, released-by)
- Equipment-out-of-service banner (reason, since, expected return)
- Service ticket card (issue, reporter, priority, assigned tech, status)
- Lost/missing asset row
- Depreciation chart card
- License/seat usage bar (for software assets — used / total + renewal)
- Asset QR/barcode label preview (printable tag layout)
- Recall notice banner (FDA recall ID, affected serials, action required)

═══════════════════════════════════════════════
PART 7 — CROSS-MODULE PATTERNS
═══════════════════════════════════════════════

These appear across multiple modules and must look identical everywhere:

- Patient mention chip (@MRN-12345678) with hovercard preview
- Staff mention chip (@Dr.Patel) with hovercard preview
- Approval card (used in PTO, shift swaps, equipment requests, consult assignments)
- Sharing dialog (specific people/roles, role chips, expiry option for temporary access)
- Permissions matrix (role × resource × action)
- Audit log row (always present — HIPAA requires it)
- Activity log row (who did what, when)
- Attachment chip (DICOM, lab PDF, scanned doc, photo) with type icon
- Saved view tab strip (custom worklists)
- Bulk-action floating bar
- Inline AI assist chip (✨ Summarize chart, ✨ Draft note, ✨ Suggest differential, ✨ Auto-code) — render as suggestion chips, never as automated actions
- HIPAA / PHI sensitivity ribbon (always-visible indicator that current view contains protected info)
- Session-context indicator (workstation ID, location — for shared device contexts)

═══════════════════════════════════════════════
PART 8 — LAYOUT OF THE CANVAS
═══════════════════════════════════════════════

- Long scrollable single canvas
- Sticky left section nav listing every Part (1–8) and major subsection — clickable
- Each section opens with H2 + one-sentence purpose statement
- Each component has a small label + tiny caption noting variants/states
- Light theme on left half, dark theme on right half — OR alternate by section, whichever reads cleanly
- Section dividers are subtle horizontal rules, not heavy bands
- Density: high but readable. This should look like a real Storybook/design-system page that a serious health-tech product org would actually use to ship to hospital customers

═══════════════════════════════════════════════
EXPLICIT DON'TS
═══════════════════════════════════════════════

✗ Do not build pages, screens, or working products
✗ Do not use lorem ipsum — every patient name, MRN, diagnosis, medication, vital, lab value must look real
✗ Do not skip states — empty/loading/error/critical are required, not optional
✗ Do not collapse domain components into a generic "card" — each module's signature components must be visibly distinct
✗ Do not use heavy drop shadows; rely on borders + subtle elevation
✗ Do not use bright saturated SaaS colors; the palette is clinical and confident
✗ Do not skip dark theme — many hospital workstations run dark for night shifts
✗ Do not minimize allergy/critical/code-status indicators — these must be visually loud and unmissable
✗ Do not use cute or playful illustrations in empty states — clinical contexts require restraint
✗ Do not use red for anything that isn't clinically critical — red fatigue is dangerous
✗ Do not generate "see Part X" placeholders — render every section in full

═══════════════════════════════════════════════
DELIVERABLE CHECKLIST
═══════════════════════════════════════════════

☐ All 8 Parts present and rendered in full
☐ All 5 module accent ramps shown
☐ All 5 modules have their signature composed components
☐ Light + dark theme visible for every component
☐ Tables shown with all sub-variants (lab results table specifically rendered)
☐ Patient banner rendered prominently — it's the most important object in the entire system
☐ Allergy band, code status pill, and isolation pill all visible and visually distinct from generic status pills
☐ Critical-alert modal rendered (drug allergy override style)
☐ Two-person verification modal rendered
☐ Vitals strip chart, lab trend chart, MAR timeline rendered as actual specimens
☐ Body diagram selector rendered as actual SVG
☐ DICOM viewer placeholder rendered
☐ HIPAA / PHI ribbon visible
☐ Audit log row present
☐ Realistic clinical content throughout (no lorem ipsum, no "Patient 1")
☐ Sticky section nav functional

Go wide. Go deep. If in doubt, add more. Healthcare UI is a domain where edge cases matter more than happy paths — surface them.