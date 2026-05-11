# Irisi

Pronounced **"Hi-ri-z."**

A slide-generation web app powered by its own React component library. The product is one stance — **maximalist startup, warm-confident.** The library underneath is *many* stances — every slide pack carries its own worldview from the catalogue.

## Why this dual structure

The product itself needs a confident, opinionated voice — so users feel they're holding something *expensive, sleek, beautiful, fast*. That's a single stance applied with discipline.

But the *output* — the slides — needs to flex. A consultant's deck shouldn't look like a kid's classroom poster. A founder's pitch shouldn't look like a research paper. The library is the catalogue of slide stances; the app is the director that picks one for you and dresses it in your brand.

## The stance — for the product chrome

- **Frame.** A confident director who knows what good looks like.
- **Surface.** Cool-neutral near-white paper (`#F7F8FB`), cool-leaning near-black ink (`#0F1115`), pure-white sheets. Light + dark from day one. Modern, premium, *fast* — not editorial, not generic.
- **Color.** Signal blue `#0361F0` as the single accent — deep, electric, confident. Sits on warm cream paper to feel premium rather than corporate. State colours used only when the meaning warrants.
- **Type.** Bricolage Grotesque (display, heavy, condensed-feel) does the impact. Inter handles the chrome. JetBrains Mono carries codes, prompts, tokens. Instrument Serif as a quiet italic for asides.
- **Motion.** 200ms ease-out. Subtle lift on hover for primary surfaces. No bounce as decoration. Slides arrive on the canvas with a single-frame fade.
- **Geometry.** Spacious. 12–24px radii on cards, 8–14px on controls. 64px page padding. Type does the heavy lifting; whitespace is the second-loudest object.
- **Voice.** First-person plural, modern, declarative. *"We design the slide. You bring the story."*

## The slide library — the catalogue

Each slide pack lives at `slides/<stance-slug>/`. A pack contains ~12 slide layouts, all in one stance:

`title` · `agenda` · `section-divider` · `big-stat` · `two-column` · `three-column` · `image-led` · `quote` · `comparison` · `timeline` · `team` · `conclusion`

We're building all 25 stances from `styles/STYLE-CATALOG.md`, plus a Maximalist-startup pack that mirrors the product's own stance.

## Surfaces (Part IV — "the things this app does that nothing else does")

- **The prompt landing.** Type-led hero, floating textarea anchored bottom, mid-page rotating slide gallery proving the library's range.
- **The question stage.** AI clarifies in a calm dialogue layout — one question at a time, generous breathing room, suggested answers as chips.
- **The highlights canvas.** Drag-rearrange slide outline cards before generation.
- **The slide preview & editor.** Full-bleed canvas, dock-rail of slide thumbs on the left, properties on the right, present + export at top.
- **The library docs.** Where developers (and AI tools) browse slide packs, copy code, drop into their project.
- **The brand wizard.** Logo / colours / fonts / tone collected with a craftsman's care.
