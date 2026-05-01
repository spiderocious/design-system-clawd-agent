# Style catalog

Twenty-five design-system stances. Each is a single, opinionated worldview — not a "theme." When the agent picks one for a project, the *whole* system bends to its rules: the canvas, the type, the chrome, the way buttons press, the way numbers shout, the way critical moments interrupt. A stance is the answer to the question "what *kind of object* is this software pretending to be?"

The agent must always pick **exactly one**. Stances may not be blended; that produces the AI-slop we are trying to escape. If the brief doesn't fit any of these, the agent invents a 26th — but it is a single thing with an answerable question, not a smoothie.

For each stance below:
- **Frame** — the metaphor; what is the software pretending to be
- **Surface** — paper / glass / matte / film / etc.
- **Color** — the palette rule (one accent or many; reserved colours)
- **Type** — family logic
- **Motion** — what's allowed, what isn't
- **Geometry** — radii, edges, density
- **Voice** — copy tone
- **Best for** — domains where this style sings
- **Avoid for** — domains where it cracks
- **Exemplars** — products / printed objects that hold this stance

---

## 1 · Surgical paper

- **Frame** — a printed clinical chart on a desk
- **Surface** — warm bone-paper (`#F4EFE6`), inverted to ink-paper for night shifts
- **Color** — one accent (apothecary green); critical-red reserved for life-threatening only; warm-leaning ink instead of cool slate
- **Type** — serif (Newsreader) for thinking, humanist sans (Inter) for chrome, monospace (JetBrains Mono) for record numbers
- **Motion** — paper turns up by 8px in 200ms ease-out; no bounce, no spring
- **Geometry** — sharp 4px on cards, 6px on controls; hairlines instead of shadows; full-width strips with rules
- **Voice** — direct, dictated; serif italic for chief-complaint quotes
- **Best for** — clinical, legal, governmental, anything where misreading hurts
- **Avoid for** — consumer playfulness, shopping, gaming
- **Exemplars** — Epic / Cerner reimagined; Penguin Classics paperbacks; hospital signage

---

## 2 · Editorial broadsheet

- **Frame** — a serious newspaper, but daily and digital
- **Surface** — paper-white (`#FBFAF7`), with deep black ink and one red rule
- **Color** — black, white, one journalistic red used only for breaking/critical; everything else in greys
- **Type** — Display serif (Tiempos / Playfair / Source Serif), narrow sans for byline (Inter / Söhne), italic serif for pull quotes
- **Motion** — print metaphors: pages turn, columns slide; nothing flies
- **Geometry** — heavy column grids; horizontal rules separate sections; no soft shadows; small caps for sections
- **Voice** — bylined, edited, present-tense
- **Best for** — long-form analytics, research dashboards, intelligence platforms, knowledge-management apps
- **Avoid for** — kid products, ecommerce checkout, transactional UIs
- **Exemplars** — NYTimes Cooking, The Browser, Bloomberg Terminal's web revisions, Stripe Press

---

## 3 · Swiss instrument

- **Frame** — a Braun calculator from 1972
- **Surface** — true white (`#FFFFFF`) or pure black; never grey
- **Color** — black-on-white; one tightly chosen accent (often safety orange or signal yellow); no semantic-colour soup
- **Type** — Helvetica Now / Inter / Söhne — *only* sans, *only* one weight per role
- **Motion** — none, or quasi-instant (≤100ms linear); no easing decoration
- **Geometry** — 4-or-8 grid, 0px corners, hairlines (1px), generous whitespace as the primary design tool
- **Voice** — terse, label-only, no sentences in chrome
- **Best for** — pro tools where users are present, daily — IDEs, audio software, data tooling, time-tracking
- **Avoid for** — onboarding, marketing pages, low-frequency consumer apps
- **Exemplars** — Linear's earliest UI, Things 3, Dieter Rams products, Vitsoe shelving system

---

## 4 · Brutalist dossier

- **Frame** — a security file, declassified
- **Surface** — concrete grey (`#E5E2DC`) with redaction-black overlays
- **Color** — black, paper, and one toxic accent (acid yellow, hazard orange) used as a redaction or alert mark
- **Type** — monospace dominates — JetBrains Mono / IBM Plex Mono — sans for body, no serif at all
- **Motion** — abrupt; cuts, no transitions
- **Geometry** — hard edges, exposed structure, visible grid, deliberate overlap, raw heading underlines, inline numeric tags `[01]`
- **Voice** — administrative, third-person, time-stamped
- **Best for** — analytics, internal admin tooling, security/audit dashboards, anti-CMS CMSes
- **Avoid for** — anything trying to feel friendly or marketed
- **Exemplars** — Are.na, Read.cv (early), Bret Victor's pages, Vercel's docs in early 2020s, Brutalist Websites archive

---

## 5 · Glassmorphic studio

- **Frame** — a control room with frosted glass between you and the data
- **Surface** — translucent panels (`backdrop-filter: blur(24px)`) layered on a saturated background
- **Color** — a single rich background colour (deep teal, indigo, rose); panels are 6–12% white over it; accents emerge from the underlay
- **Type** — humanist sans (Inter / SF Pro), tight tracking, big display weights
- **Motion** — gentle parallax, slow scale on hover (1.02), springy modal entries; respects reduced-motion
- **Geometry** — large 16–24px radii, generous internal padding, soft shadows of the underlying colour
- **Voice** — confident, marketing-adjacent
- **Best for** — consumer dashboards (mood, fitness, finance for the optimistic), creative tools, music apps
- **Avoid for** — clinical, dense data, anything for night-shift use, accessibility-critical contexts
- **Exemplars** — macOS Big Sur control center, Apple Music macOS, modern Spotify desktop

---

## 6 · Industrial telemetry

- **Frame** — the dashboard of an oil rig, a power plant, a plane
- **Surface** — true black (`#0B0B0B`) or near-black charcoal; no warmth
- **Color** — phosphor green / amber / cyan used like CRT signals; red is alarm; everything else is greyscale
- **Type** — geometric mono (JetBrains Mono / DM Mono / Berkeley Mono); single sans for chrome
- **Motion** — values *tick*, not animate; one-frame increments; gauge needles step
- **Geometry** — bezels, dials, segmented LCDs, big numbers that *shout*; 2px corners or none
- **Voice** — telegraphic, abbreviated
- **Best for** — observability, devops, energy, manufacturing, autonomous-system dashboards
- **Avoid for** — consumer, ecommerce, social
- **Exemplars** — Datadog dashboards, Grafana dark, Bloomberg, NASA Mission Control, Raycast extensions

---

## 7 · Soft Scandinavian

- **Frame** — a Nordic apartment in winter morning light
- **Surface** — off-white (`#F7F5F0`), warm pale neutrals, no pure black
- **Color** — sage, dusk-blue, mustard, blush — used in single-pigment fills, never gradients
- **Type** — humanist serif (Tiempos / Söhne) for headlines, neo-grotesque sans for body, all medium weights
- **Motion** — long, slow ease-in-out (300ms+); fades dominate over slides
- **Geometry** — generous 12–20px radii, generous whitespace, line illustration in single-stroke
- **Voice** — first-person, gentle, observational
- **Best for** — wellness, journaling, quiet-tech, meditation, finance-for-creatives, real estate
- **Avoid for** — high-stakes, urgent, dense
- **Exemplars** — Arc Browser's marketing, Headspace's recent redesigns, Linear's marketing pages, Cron / Notion Calendar

---

## 8 · Retro terminal

- **Frame** — a green-screen VT220 from 1985
- **Surface** — black (`#0A1010`) with phosphor green (`#33FF99`) text
- **Color** — green, amber, sometimes white-on-black; *one phosphor* per screen, mixed across screens
- **Type** — entirely monospace; CRT-styled (IBM Plex Mono, VT323, Berkeley Mono); ASCII box-drawing characters as separators
- **Motion** — typewriter reveal, blinking cursor, cursor-block selection
- **Geometry** — square corners (0px); exposed character grid; ASCII frames around panels (`└──`)
- **Voice** — system-prompt, all-caps prompts, `$ command` cues
- **Best for** — developer tools, indie SaaS for technical users, hacker-magazine sites, niche dev-marketing
- **Avoid for** — consumer apps, anything with visual content
- **Exemplars** — Charm.sh, Glow markdown viewer, Posthog's earliest UI, Ghostty's marketing

---

## 9 · Editorial photographic

- **Frame** — a glossy travel/architecture magazine
- **Surface** — large hero photography, bleeding to edges; off-white interior
- **Color** — neutral chrome; the photography carries the colour story
- **Type** — display serif paired with grotesque sans; large size contrast (96px headlines vs 13px captions)
- **Motion** — image parallax, gentle ken-burns, smooth scroll
- **Geometry** — full-bleed photography, narrow text columns (~50ch), italic captions
- **Voice** — narrative, atmospheric
- **Best for** — travel, real estate, hospitality, food, fashion, art galleries
- **Avoid for** — data, internal tools, anything text-heavy without imagery
- **Exemplars** — Cereal Magazine, Kinfolk, Airbnb Plus listings, Apple's product pages

---

## 10 · Transit board

- **Frame** — a Helvetica-on-black NYC subway sign or a Vignelli airline schedule
- **Surface** — pure black or pure paper; no in-between
- **Color** — coloured route-bullets used as the only chromatic device — round circles with single letters; otherwise mono
- **Type** — Helvetica / Akzidenz-Grotesk / Standard Medium; signage-grade
- **Motion** — flap-board flips for arrivals; otherwise static
- **Geometry** — heavy bullets, thick rules, generous whitespace, rule-aligned columns
- **Voice** — directive, present-tense, departure-board
- **Best for** — booking products, scheduling, logistics, anything time-tabular
- **Avoid for** — dense forms, long-form text, marketing
- **Exemplars** — NYC MTA signage, Vignelli's Unimark work, JR East's digital boards

---

## 11 · Notebook grid

- **Frame** — a moleskine dot-grid notebook with a fountain pen
- **Surface** — paper with a faint dot-grid background (10mm); ink-blue pen for handwritten elements
- **Color** — graphite black, paper, with one fountain-pen accent (royal blue / oxblood / forest)
- **Type** — humanist serif for body, italic-cursive script (Caveat / Indie Flower) used **sparingly** for annotations only
- **Motion** — pen strokes appear as if drawn (stroke-dasharray reveal); gentle
- **Geometry** — dot-grid, hand-drawn underlines and circles via SVG, organic line weight
- **Voice** — first-person, in-progress
- **Best for** — note-taking, journaling, learning tools, sketching apps, planners
- **Avoid for** — high-trust enterprise, financial precision
- **Exemplars** — Excalidraw, Heptabase, Reflect, Tana's marketing, MyMind

---

## 12 · Showroom mono

- **Frame** — a luxury watch boutique under display glass
- **Surface** — warm-grey deep neutral (`#1C1A18`) or its inverse near-paper; subtle grain
- **Color** — single high-contrast accent (champagne gold / oxblood / bottle green); whites are ivory, never blue
- **Type** — high-contrast didone display (Bodoni / GT Super), elegant grotesque body (Söhne / Suisse), italic for product names
- **Motion** — slow 400ms+ fades; almost-imperceptible parallax; never bouncy
- **Geometry** — golden-ratio grids, slim 1px hairlines in champagne, abundant negative space, large product imagery
- **Voice** — third-person, restrained, expensive
- **Best for** — luxury commerce, bespoke products, high-end real estate, fine dining
- **Avoid for** — productivity, B2B SaaS, bargain shopping
- **Exemplars** — Aesop, Rolex.com, Patek Philippe, Hermès, MR PORTER editorial

---

## 13 · Risograph print

- **Frame** — a screenprinted indie zine
- **Surface** — recycled paper texture (newsprint warm); visible halftone dots; misregister where the colours overlap
- **Color** — two flat spot colours plus paper (e.g. fluorescent pink + bottle green); never CMYK gradients
- **Type** — chunky display sans (Söhne Breit / Druk / Tusker), retro grotesque for body
- **Motion** — print-press registration shifts on hover (1–2px misalign); flip-card hovers
- **Geometry** — overlapping shapes with multiply blend modes, halftone fills, hand-set corner ornaments
- **Voice** — earnest-irreverent, indie-magazine
- **Best for** — community products, music, events, books, indie publishers, learning brands with personality
- **Avoid for** — finance, healthcare, anything that needs to read as serious
- **Exemplars** — Are.na's earlier marketing, Risotto Studio, It's Nice That, indie zine archive sites

---

## 14 · Graph paper

- **Frame** — engineer's quad-rule paper, with hand-drawn axes
- **Surface** — pale cyan grid lines (`#D4E4ED`) on cool white; major lines every 5 units
- **Color** — pencil-graphite blacks, one ink-blue accent, red for flagged values
- **Type** — engineering mono (Berkeley Mono / DM Mono); humanist sans for chrome
- **Motion** — values plot — points drop into place, lines draw left-to-right
- **Geometry** — visible grid, axes labelled, charts that look hand-drafted
- **Voice** — analytical, with units always
- **Best for** — engineering tools, scientific dashboards, structural design, lab software
- **Avoid for** — consumer-facing brands, marketing pages
- **Exemplars** — Observable notebooks, Desmos calculator, Mathematica's UI, Ben Frain's blog

---

## 15 · Liquid material

- **Frame** — Apple's iOS / macOS in 2025, "liquid glass" era
- **Surface** — glassy, translucent, refractive; backgrounds shimmer subtly
- **Color** — adapts to system theme; vibrant accents that bend light through the panels
- **Type** — SF Pro / Inter Display, with VARIATIONS used (optical sizing, weight axis)
- **Motion** — physics-based: spring damping on every interaction; haptics analogues; momentum scrolling visible
- **Geometry** — generous radii (16–28px), continuous-curve corners (`squircle`), depth via blur not shadow
- **Voice** — Apple-clean, minimal copy
- **Best for** — consumer apps that want to feel native to Apple platforms, premium consumer SaaS
- **Avoid for** — desktop-pro tools, anything that competes with the OS chrome
- **Exemplars** — iOS 17+ system apps, the new Maps, Things 4, iA Writer

---

## 16 · Bauhaus poster

- **Frame** — a 1923 Weimar exhibition poster
- **Surface** — primary-coloured fields (Bauhaus red, blue, yellow) on cream
- **Color** — exactly four colours: red, blue, yellow, black, on cream — *no others*
- **Type** — geometric sans (Futura / GT America Mono / Avenir); minimal weight variation; very tight tracking
- **Motion** — geometric: shapes rotate, scale, snap; no easing curves, all linear
- **Geometry** — circles, squares, triangles as primary motifs; visible composition — left/right balance with intent
- **Voice** — declarative, manifesto-like
- **Best for** — design schools, architecture, museums, education-with-personality
- **Avoid for** — anything text-dense
- **Exemplars** — Bauhaus Archive, Pentagram's recent work, MoMA's online presence

---

## 17 · Japanese minimalism

- **Frame** — a tea-ceremony pamphlet
- **Surface** — washi paper texture in oyster-white; vertical-rule asymmetry
- **Color** — sumi-ink black, rust-orange (`#B5573B`), sage, single point of vermillion as accent
- **Type** — Noto Serif JP feel even in Latin glyphs; tall body height; generous line spacing (1.8+); small body sizes (12–13px)
- **Motion** — almost none; brushstroke reveals; wipe transitions
- **Geometry** — asymmetric layouts, generous left margins, single-line icons drawn like brush strokes
- **Voice** — quiet, declarative, single-sentence paragraphs
- **Best for** — tea / ceramics / wellness / hospitality / hotels / artisanal products
- **Avoid for** — productivity, dense data, social
- **Exemplars** — MUJI, Aman Resorts, Toyo Ito's archives, Naoto Fukasawa's portfolio

---

## 18 · Maximalist startup

- **Frame** — Stripe / Vercel / Linear marketing pages, ca. 2023
- **Surface** — gradient-mesh hero backgrounds; white interior product surfaces
- **Color** — saturated brand gradient (3-stop) on landing; restrained chrome inside; one accent through the product
- **Type** — bold display weight for h1 (Inter Display / GT America), tight tracking; smaller weights below
- **Motion** — confident: cards lift, gradients shift, beam-reveals on scroll, small spring on press
- **Geometry** — 12–16px radii, rich shadows on landing, less inside the app; hero motion sections
- **Voice** — confident first-person plural, modern
- **Best for** — modern B2B SaaS, developer tools, infra, fintech for builders
- **Avoid for** — kids, healthcare-critical, contexts where restraint matters more than confidence
- **Exemplars** — Linear, Vercel, Stripe, Resend, Clerk, Cal.com

---

## 19 · Cartographer's atlas

- **Frame** — a 1920s railway-society atlas with hand-drawn maps
- **Surface** — cream paper, sepia inks, faint topographic contour lines as background
- **Color** — sepia browns, ink black, oceanic blue, claret accent
- **Type** — Trajan / Cinzel for major headings, Garamond / Cormorant for body, italic small caps for legends
- **Motion** — pan-and-pin: maps glide; cards reveal like turning a folded map
- **Geometry** — heavy ornamental rules, page-corner ornaments, drop caps, callout numbers in roman numerals
- **Voice** — period-correct, formal
- **Best for** — travel, exploration, museums, archives, genealogy, historical software
- **Avoid for** — modern transactional, productivity
- **Exemplars** — Atlas Obscura, Field of Vision, Dwarkesh Patel's blog, certain National Geographic special features

---

## 20 · Construction blueprint

- **Frame** — a draughtsman's blueprint laid on a light table
- **Surface** — Prussian blue background (`#0F3D5C`) with white linework; or its inverse white-on-blue
- **Color** — blueprint blue, white, single red accent for revisions
- **Type** — engineering hand letterforms (Architects Daughter, Reenie Beanie) for annotations; Inconsolata for measurements; all-caps everywhere
- **Motion** — drawing-pen reveal of lines; stamp-down for confirmations
- **Geometry** — visible measurement-tick rulers along edges, dimension lines with arrows, exposed centre-marks
- **Voice** — annotation-style, "see fig. 3"
- **Best for** — architecture, construction, manufacturing CAD-adjacent SaaS, design-tool marketing
- **Avoid for** — anything not technical-by-domain
- **Exemplars** — Figma's earliest marketing, Shapr3D, Construction-tech firms, Hubs (formerly 3D Hubs)

---

## 21 · Sushi-counter omakase

- **Frame** — a single-sheet menu at a bar with eight seats
- **Surface** — single column, white space dominant, vertical strokes only
- **Color** — black ink, washi cream, single accent (matcha / yuzu / charcoal)
- **Type** — tall narrow serif for the menu (Söhne Schmal / Sentinel Condensed) — vertical reading, tight line height
- **Motion** — elements arrive on scroll like courses being placed: one at a time, paced
- **Geometry** — narrow content column (~600px), generous vertical rhythm, no horizontal layouts
- **Voice** — single-line tasting-menu descriptions, present-tense
- **Best for** — single-page-app personal sites, photographer portfolios, indie products with one feature
- **Avoid for** — anything multi-modal, dense applications, dashboards
- **Exemplars** — Read.cv (current), Notion Bio, Linktree's premium templates done right, Suno's launch pages

---

## 22 · Mid-century playful

- **Frame** — a Charley Harper poster, a 1960s storybook
- **Surface** — warm cream with flat shapes, no gradients
- **Color** — saturated four-colour palette (mustard, teal, brick-red, navy) on cream; never digital-bright
- **Type** — geometric sans with personality (Domaine / Sharp Grotesk / Tasa Orbiter), serif italic for asides
- **Motion** — flat-shape morphs, puppet-rig animation, Lottie-style; never realistic physics
- **Geometry** — flat illustrative scenes, pictograms, decorative line ornaments
- **Voice** — warm second-person, sometimes whimsical
- **Best for** — kids products, education, hospitality, storybook brands, friendly fintech
- **Avoid for** — enterprise, anything serious
- **Exemplars** — Duolingo, Penguin Kids, Mailchimp's older brand, Uniqlo's web in 2010s

---

## 23 · Rolling-paper minimal

- **Frame** — a sheet of A4 with one mark on it
- **Surface** — pure white, edge to edge
- **Color** — black, white, and *one* single tightly-tuned accent — chosen with extreme care, used ≤ 2 places per page
- **Type** — exactly one sans family, two weights (regular + semibold), two sizes (16 + 28); nothing more
- **Motion** — fade only; 200ms; never combined with translate
- **Geometry** — no borders, no shadows, no fills; whitespace separates everything; alignment is the only grid
- **Voice** — minimal, single-sentence sections
- **Best for** — personal sites, manifestos, single-feature products, agency portfolios
- **Avoid for** — anything dense or transactional
- **Exemplars** — Frank Chimero's site, Jason Yuan's portfolio, paper.design, certain Tobias van Schneider work

---

## 24 · Soviet poster

- **Frame** — a 1925 Rodchenko constructivist poster
- **Surface** — warm cream or hammer-black; never neutral grey
- **Color** — exactly red, black, cream — sometimes plus one industrial gold
- **Type** — bold geometric sans set at extreme scales (some words at 200px, others at 14px); diagonals and rotations used
- **Motion** — abrupt slides, geometric reveals, no decoration
- **Geometry** — diagonals, photomontage, asymmetric heavy compositions; large numbers as design elements
- **Voice** — declarative, propaganda-cadence
- **Best for** — bold consumer brands with attitude, music apps, sports, certain cultural products
- **Avoid for** — restraint-required domains, healthcare, finance
- **Exemplars** — Field's earlier work, Pentagram's manifesto pieces, Aaron Lowell Denton's work

---

## 25 · Workshop manual

- **Frame** — the Haynes manual for a 1972 BMW
- **Surface** — newsprint cream with pencil-grey overlays; smudged ink feel
- **Color** — black, cream, oxidized-iron orange-brown for highlights, occasional industrial yellow
- **Type** — slab-serif (Roboto Slab / Tiempos Slab / Sentinel) for headers, sans body, mono for part numbers
- **Motion** — page-turn metaphors, exploded-view parts that animate apart on hover
- **Geometry** — exploded-view diagrams, numbered callouts, parts-list tables, fix-it stamps
- **Voice** — instructional, second-person imperative ("Loosen the…")
- **Best for** — DIY apps, repair tools, vehicle/equipment SaaS, learning-by-doing products, hardware companies
- **Avoid for** — premium luxury, health, anything not procedural
- **Exemplars** — iFixit, Common Wealth Magazine, Apartamento, the actual Haynes manuals

---

# How to use this catalog

When the agent reads a brief, it should ask itself: *"What is this software pretending to be?"* That question selects the stance.

A finance app could be #2 (Editorial broadsheet — Bloomberg-feel), #18 (Maximalist startup — Stripe-feel), or #6 (Industrial telemetry — trader desk). The brief decides which.

If the brief fits **none** of these, the agent invents a 26th — but it must answer the same questions: frame, surface, colour, type, motion, geometry, voice. A new stance is a single coherent worldview, not a remix.

Never blend stances. If the user later wants to "make the buttons more like #5 but the type more like #2," that is a sign the stance is wrong — go back to discovery.
