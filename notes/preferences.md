# Durable preferences

Things the user has consistently affirmed, across sessions or projects. Keep this short — if a note hasn't proven out across two contexts, leave it in the per-project file.

Append-only. Never delete; supersede with a new dated entry.

---

## 2026-05-01 · stance-first design

The user's strongest signal so far: **commit to one stance, never blend.** They explicitly contrasted two attempts:

- A first Medcord attempt that defaulted to Slate-grey + Tailwind-blue chrome with five module accents fighting each other → user called it "AI garbage."
- A rebuild on a single "surgical-paper" stance (warm bone-paper, ink-warm, apothecary green as the only accent) → user called it "shit this is goooood."

**Take-away.** Pick a stance from `styles/STYLE-CATALOG.md` (or invent a 26th if needed), apply it to every surface, refuse the easy defaults. The Medcord rebuild is the calibrated bar.

---

## 2026-05-01 · scenes over catalogues

The user prefers components rendered as **named situations** — "the patient banner," "the bed board," "the EMR chart open" — rather than "card variants" or "default · hover · focus · active · disabled" five-up grids.

**Take-away.** Every project's surfaces section is at least three scenes. State grids exist only as a small reference at the end of a primitive page, not the main event.

---

## 2026-05-01 · type does work

The user noticed and approved: a serif for thinking (Newsreader / similar), a humanist sans for chrome (Inter), a monospace for record-numbers (JetBrains Mono). Tracking actually used — display tightened, labels opened, overline at +0.18em.

**Take-away.** A two-or-three family pairing with deliberate tracking is part of the stance, not a token afterthought.

---

## 2026-05-01 · numbers shout

In Medcord the vital readouts use 26–40px tabular monospace. The user singled this out approvingly.

**Take-away.** When a number is the most important thing on the screen (vitals, prices, bed counts), make it *visibly the loudest object* — large mono, tabular, terse unit small beside it.

---

## 2026-05-01 · red is reserved

Critical-red used only for life-threatening / irreversible. Amber for everything else warning-level. The user appreciated this discipline because it lets red retain its meaning.

**Take-away.** Default to amber for warnings; reserve red for the moments that genuinely need it; never use red as decoration.

---

## 2026-05-01 · hairlines, not shadows

Medcord uses 1px borders and the rare heavy ink-rule for separation. Drop shadows are reserved for popovers and modals only, and even then they stay shallow.

**Take-away.** When in doubt, draw a line. Shadows are a last resort.

---

## 2026-05-11 · variations are read per-component, not per-package

Across two projects now (medcord and pracket), when shown A/B/C variations of signature components, the user accepts the *stance* in one click but then dissects the package: "I like A for everything except the list row — give me three alternatives just for that." On pracket they swapped the profile card to B's design while keeping the rest of A, then asked for A1/A2/A3 inside the same `_variations.html`.

**Take-away.** Build `_variations.html` so it can host *sub-variations of a single specimen* without redoing the whole file. After the first pick, expect a "redesign just this one" request and treat it as normal flow, not a setback.

---

## 2026-05-11 · "lock it in, what's next?" means run, not deliberate

When the user says they're ready to lock the design, the appropriate response is to outline the Act IV plan in 3–5 bullets, confirm the remaining ambiguities (currency, scenes), and then build without check-ins between specimens. On pracket this meant batching foundation → primitives → scenes → overlays → register into one continuous run, surfacing progress at section boundaries only.

**Take-away.** Mid-build interruptions to ask "shall I do X next?" break the user's trust that the agent has a plan. Confirm once, then commit.

---

## 2026-05-01 · plain language

The user is non-technical and prefers plain explanations. They paste in voice notes, ramble, brainstorm. Don't expect formatted PRDs.

**Take-away.** When asking discovery questions, translate jargon. *"What the page is trying to feel like"* not *"what's the design language."* When showing variations, label them A/B/C with a one-sentence caption, not "variant token primary v2."
