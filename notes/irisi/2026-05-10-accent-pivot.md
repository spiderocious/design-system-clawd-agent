---
name: Irisi accent pivot
description: User rejected burnt amber in favour of signal blue #0361F0 mid-build
type: project
---

# 2026-05-10 — accent pivot

The first build of Irisi shipped with **burnt amber `#C56C0A`** as the single product accent. The user reviewed the landing page, said *"i love it. continue,"* — but on continuation explicitly asked to swap the brand colour: *"the color of the product is not one that i love, i.e the branding ... instead of the amber color, i'll prefer something deep green or deep blue (like #0361F0)."*

**The fix.** Foundation `--accent-*` ramp rebuilt around `#0361F0` (signal blue). Legacy `--amber-*` tokens kept as aliases so any slide pack or surface that already referenced amber re-resolves to blue without rewriting markup. Selection, focus rings, and shadow-coloured RGB values updated to match. Project tile in `projects.json` and root `index.html` re-tagged.

**Why:** the rest of the design (type, geometry, density, motion) the user "loved" — only the brand colour failed. The pivot is colour-only, not stance.

**How to apply:** when in doubt about warm-vs-cool brand colour for a confident-modern product, lean cool/electric (signal blue) over warm (burnt amber). Warm-confident is still the *paper-and-ink* combination — cream + near-black — but the accent should signal "premium tech tool," not "artisan workshop." On future projects with similar briefs, propose the cool-saturated option first.
