# Solon — discovery decisions (2026-05-11)

Brief delivered as a written MVP spec at `projects/solon/mvp.md`. Five modules: a flagship Election Simulator (Module 0), Voter Data & Segmentation (1), Agent & Volunteer Coordination (2), Finance & Compliance (3), Election-Day War Room (4). Nigeria-specific (INEC, NDPR, BVAS, EC8A, NIN, multi-language).

User pre-specified:
- Palette: deep forest green `#1B4332`/`#2D5A3D`, cream `#F5EFE0`, burnt orange `#C7522A`, charcoal / off-white neutrals.
- Type: Fraunces + Inter.
- Name: Solon — wisdom, reform, political neutrality.

Discovery answers:
- **Tuning bias:** hold both equally — editorial gravitas in Simulator scenes, instrumented density in War Room scenes.
- **Orange role:** alerts ONLY. Green is the CTA / interactive accent. Matches the "red is reserved" preference; gives orange real semantic load.
- **Hero scenes (4, not 3):** Simulator scenario builder, constituency intelligence map, election-day War Room, finance compliance dashboard. User picked all four — they all matter equally.
- **AI voice:** Neutral analyst — third-person, hedged, citation-heavy. "The model attributes…" Matches Solon's neutrality positioning.
- **Mode:** light only. War Room ships light too (decision: lean into the editorial-instrument tension; revisit if user reverses).
- **Numbers:** mono for record / serif for projection. Semantic split — fact vs estimate. Mono shouts on counts; Fraunces tabular handles model projections.
- **References (all four picked):** Economist/FT, Bloomberg terminal, INEC publications, Atlas Obscura / parliamentary order paper. Stance must reconcile all four without blending — pointing at "Editorial broadsheet" (#2) with an instrumented terminal underbelly and INEC-official compliance idiom.

Implications for build:
- Four hero scenes instead of three. Plan Act IV accordingly.
- Compliance exports (INEC report PDF, EC8A capture audit) get a deliberately "official document" treatment — stamp, signature line, footer disclosure.
- AI copilot panel needs to render citations inline. Every projection carries its confidence band.
- Mobile citizen-reporter flow is in the spec but NOT a hero scene — render as a small specimen.
