# How to take notes

This folder is the agent's memory. The user can read it, but the agent maintains it.

---

## What to write down

**Yes, write a note when:**

- The user says "I love …" / "I hate …" — capture both, verbatim if possible
- The user reverses a decision mid-session ("actually, scratch that, do it the other way")
- The user vetoes a style, colour, or pattern ("not Bootstrap blue", "no glassmorphism")
- The user surprises you (rejects a "safe" choice; accepts an unconventional one)
- The user names a reference product they love or hate
- A pattern crosses two projects (mention it in `preferences.md` and tag both project names)

**No, don't bother when:**

- It's a routine acknowledgement ("yes, do that")
- It's a project-specific fact that doesn't generalize ("Medcord uses green") — that goes in the project's README
- It's something already in `CLAUDE.md` or the style catalog
- It's a one-off that won't matter on the next project

---

## Where to put it

| Kind                                                | File                          |
|-----------------------------------------------------|-------------------------------|
| Durable preferences across all projects             | `notes/preferences.md`        |
| Things the user has explicitly rejected             | `notes/rejected.md`           |
| Reference products the user loves                   | `notes/loves.md`              |
| Project-specific lessons                            | `notes/<slug>/lessons.md`     |
| A heated debate during a session — paste the gist   | `notes/<slug>/debates.md`     |

---

## Format

**Append-only.** Never delete a past entry; if it's reversed, write a new entry dated today and reference the prior. The history is the value.

**Each entry is dated and short.** One paragraph max.

```markdown
## 2026-05-01 · medcord
User rejected the slate-grey/Bootstrap-blue defaults outright. Quoted: "compare what
you built to Lumen — it's the most AI shit ui design I've ever seen." Take-away:
when in doubt, pick a stance from the catalog and *commit*; do not default to
Tailwind colours. Reference: Lumen used warm-cool tension and a single accent.
```

```markdown
## 2026-05-01 · cross-project
User likes when scenes are *named situations* — "the patient banner," "the bed board" —
not "card variants." Carry forward: every project's surfaces should be specific
moments, not generic templates.
```

---

## Read on session start

Every time the agent opens this folder, **before** responding to the user:

1. Read `notes/preferences.md`
2. Read `notes/rejected.md`
3. If continuing a project, read `notes/<slug>/`

If a relevant note exists, work it into the response naturally — don't be performative ("I see in my notes that…"); just *act on* it.
