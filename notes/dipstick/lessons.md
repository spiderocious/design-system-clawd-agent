# Dipstick — per-project notes

## 2026-05-11 · brief shape

User's brief was extremely terse — "a simple product that enables filling station owners to manage it properly. they can own multiple branches, they can manage each branch. nigerian context. you can figure out the features yourself."

I leaned in on the Nigerian forecourt vocabulary unprompted (NUPENG, NNPC, PMS/AGO/DPK, naira, dip, attendant, tanker waybill) and the user did not push back. **Take-away:** when a user invokes the agent with "Nigerian context" as the only constraint and asks me to figure out features, deep domain-specificity is the right move — generic petrol-station software would have been a worse answer.

## 2026-05-11 · user redirected the signature surface

I proposed three signature-moment options (end-of-shift reconciliation, morning roll-up, tanker delivery). User answered "all, and a lot. but i dont want hardware connections or so, also no transfers/pos linking too. just something simple, managing staffs, managing entries, liter left, dip. stock management (based off manager's entries)."

This re-framed the entire product from a *real-time telemetry / fraud-detection* system into a *structured digital logbook* — discipline through audit & posting mechanics, not through hardware ground-truth.

**Take-away:** when the user simplifies scope, don't try to smuggle the rejected complexity back in. The product is the manager's exercise book, not Datadog.

## 2026-05-11 · name chosen by user

I offered Fillup (recommended), Ledger Station, Dipstick, or "pick for me." User picked **Dipstick**. Pleasantly opinionated choice — mechanic-coded, owns the most fraud-prone moment in the business.

## 2026-05-11 · stance was uncomplicated

User asked for "confident modern SaaS" with QuickBooks/Xero as the reference (over Paystack). I proposed three stances all of which were Ledger broadsheet variants (warm cream + Source Serif 4 + Plex Mono · cream + Newsreader · cool stone + Fraunces). User picked **A — Ledger paperback** with no tweaks. Fast move.

## What worked

- Tabular monospace at every size for numbers — the page reads like a clean ledger column.
- Oxblood `#9A1F18` for shortages reads serious without being Bootstrap-red.
- Deep emerald `#0E5C3A` rather than pump-green / NNPC-green dodges the obvious cliché.
- The CRITICAL void-modal idiom (hazard stripe + typed VOID) is the right discipline for a money-trust product.
- Product chips (PMS / AGO / DPK) as small inline marks rather than chromatic fills.

## What to remember next time

- When the user gives a non-technical brief about a localised product (Nigerian, in this case), local vocabulary is part of the design. The forecourt scenes use Mokola / Surulere / PH-Rumuola, ₦196/L for PMS, NUPENG dues, NNPC, tanker waybill numbers. This was not asked for and not pushed back on.
- "All of them" as a signature-surface answer means *the day-book itself is the product* — every other scene is a view on the day-book.
