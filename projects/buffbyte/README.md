# BuffByte — warm-coach

**A redesign of [buffbyteai.xyz](https://buffbyteai.xyz/).** AI content analysis for creators — paste a draft, get a score, sentiment, virality, brand, platform, timing, risk, tips — plus a teleprompter for video scripts and a live trending board.

## The stance

**Warm coach.** A custom 26th stance (none of the 25 in `styles/STYLE-CATALOG.md` fit cleanly).

> The app is a literate friend who has read your draft and is leaving notes in the margin of a paperback book — but the friend is using a cursor.

The current product (sky-blue gradients, six rainbow feature cards, soft-blue progress bars, gradient hero text) reads as the AI-SaaS template. The redesign throws all of that out:

- **Warm paper canvas** (`#FAF7F2`) instead of cool slate.
- **Graphite ink** (`#1C1B19`), not cool grey.
- **One product accent** — violet-blue `#533AFD` — cool against the warm canvas. The contrast is intentional: the canvas reads editorial, the accent reads digital.
- **Semantic palette only**. Violet for primary / positive / interactive. Amber `#C28A2C` for warnings. Oxblood `#A0413A` for irreversible. Never bright red. No decorative tint.
- **One type family** — Inter, three weights (400/500/600), tabular figures for numbers.
- **Hairlines, not shadows.** Shadows reserved for popovers, modals only.
- **Coach voice** throughout. The AI speaks in the second person: *"Your hook lands. Tighten the middle."* Not "Hook strength: 76%."

## The two heroes

The brief asked for **two signature surfaces** — Dashboard (daily check-in) and Analysis Result (the work). Both built:

- [Dashboard](preview/30-dashboard.html) — welcome card on ink, latest analyses, quick actions, trending now, live insight callout.
- [Analysis result](preview/31-analysis.html) — 220 px score ring, the coach's quote, dimension breakdown rings, six annotated coach notes, the original draft inline-highlighted, sentiment / brand / virality / timing meta.

Plus three more scenes to prove the system:

- [Script analysis](preview/32-script.html) — line-by-line pace markers, energy timeline, pronunciation challenges.
- [Content library](preview/33-library.html) — filtered list of drafts with score rings, sparklines, status.
- [Trending board](preview/34-trending.html) — featured topic on ink, ranked list, format insights.

And a distinct **performance mode**:

- [Teleprompter](preview/43-teleprompter.html) — own rules. Ink-black canvas, oversized warm-paper type, live coach overlay. Same family scaled up.

## The signature device

The **score ring** is BuffByte's signature data device. One number, large, tabular Inter — ringed by an arc — used at three sizes (200 px hero, 88 px card, 40 px inline). Colour follows meaning: violet for good, amber for warn, oxblood for critical. See [preview/20-ring.html](preview/20-ring.html).

## Layout

```
projects/buffbyte/
├── index.html              · the project's own gallery shell
├── thumb.html              · 160×100 tile for the root gallery
├── _variations.html        · the act-III pick (A locked, accent shifted)
├── README.md
├── original-prompt.md
└── preview/
    ├── _foundation.css     · the single source of truth for tokens
    ├── _app.css            · shared app chrome (sidebar, topbar) for scenes
    ├── 01-palette.html ... 05-icons.html       · Part I · Foundation
    ├── 10-buttons.html ... 13-pills.html       · Part II · Primitives
    ├── 20-ring.html ... 25-empty.html          · Part III · Data & state
    ├── 30-dashboard.html ... 34-trending.html  · Part IV · Surfaces
    └── 40-modals.html ... 43-teleprompter.html · Part V · Overlays & performance
```

## Don'ts (project-specific)

- No gradients. None. The current product's #1 problem.
- No mono font in chrome or numbers — use Inter tabular figures. Non-technical user; mono reads "engineering."
- No multi-coloured feature cards. The current product is six pastel cards in a row — gone.
- No pill nav floating in the centre-top. Sidebar nav is the chrome.
- No emoji as icon. Single-stroke 1.5 px SVG only.
