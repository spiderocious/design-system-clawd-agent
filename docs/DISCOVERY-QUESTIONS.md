# Discovery questions

Eight to ten questions, run in order. Adapt wording to what the user already gave you. Don't re-ask things you already know.

The user is **non-technical**. Avoid jargon. Speak plainly.

---

## 1 · "What is this thing, in one sentence?"

Get the elevator pitch in their own words. If they wrote a long PRD, ask them to compress it. The one-sentence version is the agent's lodestar — every later decision should serve it.

> Branch — if they say "uhh, idk, here's what I have…" — read what they wrote, then say it back to them in one sentence and ask "is that right?"

## 2 · "Who is sitting at the screen, and when?"

Not a persona slide — a real person, a real moment. *"A nurse at 3am at the charge desk."* *"A retail trader checking their phone before market open."* *"A homeowner on the couch comparing two contractors."* The moment shapes the stance more than the demographic.

> Branch — if they describe two very different users, ask which one is the **harder** to design for. That one wins. The other gets it for free.

## 3 · "What's the moment they want to be in this product?"

What's the feeling at the centre? Calm? Confident? Powerful? In control? Curious? Nostalgic? Rushed-but-safe? There's no wrong answer; pin it down to a word or two.

> Branch — if they say "modern" or "clean" or "professional" — push: those are escape words. Ask "modern *like what* — like Stripe? like a Swiss watch face? like a 1970s scientific calculator?" The answer is what you actually need.

## 4 · "Show me one product they already love."

A reference. A real existing thing — a website, an app, a printed object, a magazine, a poster. *Why* do they love it? Often the user can't name a stance but they *can* name a product. Use that to triangulate.

> Branch — if they name three or more, ask them to pick the **one** they'd rip off if they had to. That's the gravitational centre.

## 5 · "What's the brand colour, if you have one?"

Just hex. If they don't have one, skip — you'll pick from the catalog. If they do, write it down and ask: "is this colour load-bearing — must we use it — or is it just where we started?" *Load-bearing* means the stance has to accommodate it. *Where we started* means you're free to refine.

> Branch — if they show a logo, ask if there's a brand-guide doc. If yes, read it. If no, work from the logo alone.

## 6 · "What does this product do that nothing else does?"

The differentiator. Often the user describes their product as "X for Y" (Notion for nurses, Stripe for hairdressers). The differentiator is what's *not* in that comparison. This becomes the surface that gets the most design love — the signature scene.

> Branch — if they can't name one, ask: "what would a competitor's user be jealous of when they see your product?"

## 7 · "What's the worst thing that could happen on this screen?"

Reveals the safety bar. For a banking app: a wrong transfer. For a clinical chart: a wrong drug. For an ecommerce checkout: an abandoned cart. The worst-case shapes the *critical* idiom — the irreversible button, the override modal, the audit log, the confirmation pattern.

> Branch — for low-stakes products (toys, reading apps, social), the user will say "nothing really." That's the answer; you can ease off the gravity.

## 8 · "Density — packed or spacious?"

Show them a real example: open Medcord's bed-board (`projects/medcord/preview/31-bed-board.html`) for **packed**; open Aesop.com for **spacious**. Ask which feels more like *their* product. If they want both ("packed for the dashboard, spacious for the marketing page"), confirm and remember — the same stance can carry both.

## 9 · "Light, dark, or honest about both?"

A fork. Some products are explicitly one (Linear is dark; Aesop is light). Others must do both well (anything used in a 24-hour environment). Ask. The answer changes how you build the foundation.

> Branch — if they say "dark," ask if it's **night-shift dark** (Medcord, Datadog) or **luxury dark** (Showroom mono, Apple TV). Different families.

## 10 · "Anything we should *never* do?"

The escape hatch. Lets the user veto patterns they've seen and hated. *"No stock photography of diverse people pointing at laptops."* *"No glassmorphism."* *"No Bootstrap blue."* *"No emojis as icons."* Capture verbatim into `notes/rejected.md`.

---

## After the questions

Recap to the user in one paragraph: *"Here's what I heard — you're building X for Y, the moment is Z, you love product A, your brand colour is #XXXXXX, the worst case is W, you want it dense in the app and airy in marketing, dark-only because of night-shift use, and you never want to see B or C. Did I get it?"*

Wait for confirmation. Then move to **Act II — Style proposal**.
