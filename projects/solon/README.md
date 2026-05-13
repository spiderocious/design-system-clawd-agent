# Solon

A political intelligence and campaign platform for Nigeria, designed as a parliamentary order paper.

## Stance

**Parliamentary order paper** (stance #2, *Editorial broadsheet*, extended with Atlas Obscura ornament and a Bloomberg-instrument underbelly).

The system is a printed broadsheet read in daylight by serious people — aspirants, strategists, campaign managers, finance officers. It carries gravitas in the Simulator and the export sheet; it carries instrumented density in the constituency map and the War Room. One stance, two registers.

## Tokens

- **Paper** `#F5EFE0` (cream order-paper)
- **Ink** `#1A1714` (warm near-black)
- **Forest** `#1B4332` (the one accent — CTA, link, focus, hold tier)
- **Orange** `#C7522A` (warn / toss-up / flagged, never CTA)
- **Oxblood** `#8B1A1A` (irreversible only — VOID, account suspension)
- **Fraunces** + **Inter** + **JetBrains Mono**

## The semantic rule that does real work

**MONO is record. SERIF is projection.**

- `1,284` (mono, tabular) = a counted, signed number from Form EC8A.
- `47.2% ± 3.1` (Fraunces) = a modelled estimate from Solon.

The reader can tell at a glance whether a number is a fact or a model output, without having to read a label. Every screen in the system follows this rule.

## Four hero scenes

1. **Simulator scenario builder** — race picker, candidate matchup, lever panel, projection card with confidence band, AI copilot citation block in the right rail.
2. **Constituency intelligence map** — every PU in Anambra Central coloured by win-probability tier, with drill-in card showing the top three drivers.
3. **Election-day War Room** — ink-on-cream chrome with an inverted counts strip; live tally, incident feed (sev 1–5), anomaly flags.
4. **Finance compliance dashboard** — INEC statutory cap as masthead, sub-cap bars, anomaly feed, donor risk register, signed signature block.

## Solon's AI voice

**Neutral analyst.** Third-person, hedged, citation-heavy. Every model claim carries a footnote linking to the source corpus. Voter-suppression queries are blocked at the model layer and logged.

## What didn't make Studio (deferred)

- Module 2 surfaces: agent roster grid, training-readiness dashboard, route view. Designed in primitives (PU code input, OTP, severity slider) but not as full scenes.
- Dark mode for the War Room. Decision documented in `notes/solon/discovery-2026-05-11.md`: ship light-only; revisit if the user reverses.
- Public War Room view. Spec'd in MVP but the design idiom is "same War Room with the agent identities masked and a permalink banner" — visible derivation rather than a separate scene.

## Decisions worth remembering for the next session

- Forest **is** the CTA. Orange never becomes a button background.
- The instrument input prefix (`CON ▸`, `PU ▸`, `₦`) lives on global / search / chrome inputs. Forms use the plain box with a label above.
- The brand drop-cap `S.` with an orange period is the only place orange is used decoratively — and only in masthead positions.
- The INEC export sheet uses real "official document" idiom: 3-pixel double rule under the masthead, signed/void stamps, drop-cap intro, two-column disclosure block. Don't soften it — the gravitas is the point.
