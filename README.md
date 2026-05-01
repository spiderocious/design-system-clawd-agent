# Studio · design-system playground

A folder you drop a Claude Code agent into to design a complete design system from a one-paragraph idea.

---

## Install

```bash
git clone https://github.com/spiderocious/design-system-clawd-agent.git studio
cd studio
open index.html        # see the gallery (Mac); on Linux: xdg-open · on Windows: start
claude                 # open Claude Code in this folder
```

Then in Claude Code, run `/design-system-agent` and follow the prompts.

You'll need [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed. Nothing else — no Node, no build step, no server. The whole playground is static HTML.

---

## Open it

Open `index.html` in any browser. You'll see a gallery of every project that lives here, each rendered as a small framed plate with a thumbnail of its signature component. Click a tile to enter that project's full system.

The first project on the shelf is **Medcord** — a hospital-management design system in the "Surgical paper" stance. It's the calibrated bar; refer to it.

---

## Make a new design system

In Claude Code, run:

```
/design-system-agent
```

The agent will ask you 8–10 questions (what you're building, who it's for, the moment, a reference product you love, a colour if you have one, and so on), then propose three stances from a 25-style catalog, then show you three side-by-side variations of the signature components so you can lock the look, and *then* it builds the whole system into `projects/<name>/` and registers it on the gallery.

You can also pass a one-liner:

```
/design-system-agent design a fintech app for retail traders
```

The agent will use that as a starting point and skip the questions you've already answered.

---

## What the agent reads (in order, every session)

- `CLAUDE.md` — the operating manual (discovery script, build rules, file conventions)
- `notes/preferences.md` — durable preferences across all your projects
- `notes/rejected.md` — things you've said no to before
- `projects/projects.json` — the existing shelf
- `styles/STYLE-CATALOG.md` — the 25 stances

It'll also write to `notes/` whenever you say something worth remembering.

---

## File map

```
/                         the playground
├── index.html            the gallery
├── CLAUDE.md             the agent's manual
├── styles/               the 25-stance catalog
├── docs/                 discovery questions & component checklist
├── notes/                durable preferences, rejections, per-project lessons
├── projects/
│   ├── projects.json     gallery manifest
│   └── medcord/          the reference project
└── .claude/              slash command + permissions
```

---

That's it. Drop the prompt, get a design system.
