---
name: Irisi build complete
description: Notes from the original Irisi build — what shipped, what surprised, what to remember for the next project
type: project
---

# 2026-05-10 — Irisi build complete

The full Irisi design system shipped: product (foundation, primitives, data, surfaces, overlays) plus the entire 25-stance slide library with 12 layouts each — about 33 product surfaces and 300 slide layouts total.

## What worked

**Dual-stance architecture.** The user named the *real* design problem on their own: the product itself is one stance (Maximalist startup × signal-blue), but the slide *library* is a catalogue of all 25 stances. Each pack inhabits its stance fully. That structural insight was the unlock — once we landed on it, every subsequent decision became easier. **How to apply:** when a brief is a *creator tool* (the product produces design artefacts), expect the user to want this distinction and propose it as Question 4 of discovery, not as a late-stage clarification.

**Cool-neutral paper after a colour pivot.** First build was warm cream + burnt amber. The user loved the type and structure but rejected the brand colour mid-build, asking for deep blue (#0361F0). On the swap, we also re-toned the paper and ink from warm to cool — keeping near-white but adding a faint blue undertone (#F7F8FB / #0F1115). The cooler paper made the blue read as *premium tech* rather than *editorial*. **How to apply:** if accent colour changes mid-build, audit the paper/ink temperature too — warm-cool tension between paper and accent can break the stance.

**Slide library as a scrollable single-page-per-pack.** Rather than one HTML file per layout (which would have been 300 files), each pack is one HTML file with the 12 layouts stacked. Keeps file count manageable, gives the user a scrollable preview, and matches how a real React library would expose them.

## What surprised me

**The user wanted *all 25 packs* with full layouts, not just 5–6.** I proposed a launch set; they said no, do all 25 — "ensure it's accessible for preview and can be seen in the projects list." This shifted the build budget significantly. **How to apply:** when a user is enthusiastic about an inventory ("all of them"), take it literally and front-load the breadth even if depth-per-item drops slightly. They will trade a bit of layout polish for the complete library.

**Real-time review checkpoints saved the build.** The user reviewed twice mid-build — once after the landing page, once after surface 31 — and on both occasions raised colour/paper concerns that would have required rework if they'd waited. **How to apply:** for any large multi-hour build, build the most opinion-bearing surface first (here: the landing page), get a checkpoint, then proceed.

## Decisions worth remembering

- **Brand colour:** signal blue `#0361F0` — the user explicitly preferred it over burnt amber. Future warm-confident briefs should propose deep blue or deep green as the first option, not amber.
- **Paper/ink:** cool-neutral `#F7F8FB` paper, `#0F1115` ink. Pure-white sheets inside on cards. User said "B + somewhat C" when given three paper options — i.e. cool-neutral with a hint of pure-white.
- **Type:** Bricolage Grotesque (display) + Inter (chrome) + Instrument Serif (italic-only asides) + JetBrains Mono (record). User explicitly said *don't switch the typography* during the colour pivot — that pairing landed.
- **Density:** spacious throughout. Editor allowed denser, but landing/pricing/library all generous.
- **Pronunciation:** Irisi is "Hi-ri-z" — preserve the `/Hi-ri-z/` annotation in the brand mark.

## What's still rough

- A few of the slide packs (08 retro-terminal, 15 liquid-material, 25 workshop-manual) are flagged "beta" in the library index — they ship at the same depth but use less common typefaces/effects that need more polish.
- Slide library index could grow a "filter by use-case" later (board, pitch, education, internal).
- The `--amber-*` token aliases in the foundation CSS still exist for backwards-compatibility with the early surfaces — should rename to `--accent-*` cleanly when there's room.
