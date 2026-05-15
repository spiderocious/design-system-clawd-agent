# Pracket

A tutor-meets-student marketplace where tutors publish a rich profile (credentials, evidence, location, photo, blog) and parents or students pay a one-time connection fee to message them. Identities are partially masked — first name + last initial only — to keep contact on-platform.

**Stance:** #7 Soft Scandinavian. Warm oat paper, single forest accent (`#3BB75E`), spacious lists, hairlines instead of shadows. Light only.

---

## The three signature surfaces

1. **Search results** — a Sunday-evening parent browsing for "Further Maths near Lekki." Lean-line tutor rows (A1 from the variation pick), a quiet filter rail, and a sage curation banner that tells the parent why a given tutor is first. (`preview/30-search-results.html`)
2. **Tutor profile** — Marcus K.'s full page. Hero with masked name + verified mark + italic-serif teaching philosophy; stats strip; printed-CV credentials; the tutor's own Sunday note as proof-of-thought; a sticky right rail where the **Connect — ₦2,500** action lives. (`preview/31-tutor-profile.html`)
3. **Conversation (post-connect)** — masked username at the top, the safety banner explaining the redaction rule, a thread with phone numbers shown struck-through, and a composer that warns about masking inline. (`preview/32-conversation.html`)

## The critical modal

`preview/40-connect-modal.html` — the irreversible money moment. Heavy total rule on the receipt, brick-red acknowledge step, action button restates the consequence in its label ("Connect — ₦2,750", never "Confirm").

## Decisions worth remembering

- **`#3BB75E`** is the brand and the sole accent. Sage neutrals (`green-100` / `green-200`) carry verified state. Sage paper (`green-50`) carries success.
- **No stars, no badges, no streaks.** Trust is carried by the `<span class="verified">Identity verified</span>` capsule and by credentials typeset as a printed CV.
- **Tutor names** are masked (first + initial) in every public surface. The full legal name lives only with the verification team.
- **Two prices, never confused:** the lesson rate (paid to the tutor) and the connection fee (paid to Pracket). They sit on the same rail but are separated by a hairline.
- **The conversation is the safety perimeter.** Contact info is redacted (`[redacted phone]`) until both sides press "Share contact." The banner above the thread persists while masking is on.
- **Multi-country in data, ₦ in design.** Price component is currency-agnostic; the design uses Naira throughout for now.

## Don't drift

- No glassmorphism, no gradients on cards, no five-stars, no flame-streak icons.
- The accent never appears on more than one element per visible block.
- The CRITICAL modal is the only place red carries an action; everywhere else, amber.
- The list row is the A1 lean-line locked in Act III — never re-introduce the photo-card variant for the search results.

---

*Built in the playground · `/design-system-agent` · 2026-05-11.*
