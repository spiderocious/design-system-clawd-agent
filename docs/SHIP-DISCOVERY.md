# Ship · discovery questions

Eight questions, run in order, after Act I (calibration). Each has a sane default inferred from calibration; user can press enter to accept.

The user is **non-technical-leaning**. Translate jargon. *"Where do components live"* not *"resolve module entry path."*

If a question has been answered confidently by calibration, **skip it** — don't re-ask. Just confirm in the recap at the end.

---

## 1 · "Where should the components go?"

Path inside the target repo. Default from calibration (e.g. `src/shared/ui/`). Common alternatives: `src/components/ui/`, `src/components/`, `app/components/`, `src/lib/ui/`.

Format: relative to repo root.

> Branch — if the repo has multiple component folders (`src/components/`, `src/shared/ui/`, etc.), surface them and ask which one. Don't pick.

## 2 · "What import alias do they use?"

Read from `tsconfig.app.json` / `tsconfig.json` / `vite.config.ts`. Common: `@shared/*`, `@/*`, `~/*`, `@components/*`, none-at-all-relative-imports.

Confirm: *"I'll import from `@shared/ui/button`. OK?"*

> Branch — if no alias is configured, ask if you should add one or use relative imports throughout. Adding an alias touches `tsconfig.json` and possibly `vite.config.ts` — show the diff before writing.

## 3 · "How are components organized — a folder each, or one file each?"

The two common shapes:

- **Folder-per-component.** `button/button.tsx + button/index.ts`. Reasonable when components have tests, stories, or sub-components.
- **Single-file.** `Button.tsx` (or `button.tsx`) at the components root, no folder. Simpler when components are small and self-contained.

Default: whatever calibration found. If empty, default to **folder-per-component** (matches Medcord's existing pattern, leaves room to grow).

> Branch — if calibration finds **mixed** layouts in the same repo, ask the user which to follow.

## 4 · "Styling — Tailwind, CSS modules, styled-components, vanilla, or unstyled headless?"

The big fork. Each path produces a very different output:

- **Tailwind.** Class strings. Reads `globals.css` for CSS-var tokens. Lightest weight. Best when the repo already has Tailwind.
- **CSS Modules.** `.module.css` next to each component. Tokens via CSS vars or imported. Heavier per-component but isolates style.
- **Vanilla-extract** (or similar zero-runtime CSS-in-JS). TypeScript stylesheets. Tokens via theme contracts.
- **styled-components / Emotion.** Runtime CSS-in-JS. Tokens via `ThemeProvider`.
- **Unstyled headless.** No styles shipped. Components are behavior + ARIA + class-name hooks; consumer styles. Best for "design-system-as-headless-lib" cases.

Default from calibration. If the repo has none yet, default to **Tailwind** (most common; lightest; matches the Studio's HTML output most directly).

> Branch — if Tailwind, ask follow-up: *"Extend the existing `tailwind.config`, write a fresh one, or add tokens to `@layer base` only?"* — default **extend**.

## 5 · "Class-composition utility?"

If styling = Tailwind, components need a way to merge class names. Options:

- **`cn`** — most common, often a thin wrapper around `clsx` + `tailwind-merge`
- **`clsx`** — minimal; doesn't dedupe Tailwind classes
- **`tailwind-merge`** alone — dedupes, doesn't handle conditionals as ergonomically
- **Hand-written template literals** — no util needed; OK for tiny systems

Default: from calibration. If the repo already imports `cn` from somewhere, use that path. If nothing's there, default to writing `<path>/utils/cn.ts` with the `clsx + tailwind-merge` pattern.

If styling ≠ Tailwind, this question is N/A — skip.

## 6 · "Export style — named, default, or both?"

- **Named** (`export const Button = …`) — preferred by most modern React codebases; better for tree-shaking and refactor tools.
- **Default** (`export default Button`) — older convention; some teams still use it.
- **Both** — belt-and-suspenders; some libraries do this for compatibility.

Default: from calibration. If empty, default to **named**.

## 7 · "Fonts — install via @fontsource, link to Google, or assume the host app handles it?"

The Studio HTML uses `@import url('https://fonts.googleapis.com/...')` directly. That's not how most React apps handle fonts.

- **`@fontsource/<font>`** packages — `pnpm add @fontsource/inter`, then `import '@fontsource/inter'` in `main.tsx`. Most common. Self-hosted, no runtime fetch.
- **Google Fonts `<link>` in `index.html`** — works, but introduces a network dep.
- **Host app handles fonts** — the design system doesn't ship fonts; it expects them to be loaded already. Best for libraries.

Default from calibration. If `@fontsource/*` already in `package.json`, use that. If `index.html` has Google Fonts link, mirror. If neither and the repo is going to *use* this lib (not publish it), default to **`@fontsource`**. If it's going to be published as a library, default to **host app handles**.

> Branch — if @fontsource path: confirm before running `pnpm add` / `npm install` / `bun add`. Show the exact command. Decline = write imports but skip install.

## 8 · "Do you want me to write tests alongside components?"

Default: **no.** (Per `notes/preferences.md` — and matches the existing `medcord-ui` button which has no test next to it.)

If calibration finds tests next to components (e.g. `button.test.tsx` exists), default flips to **yes** — and ask which framework (Vitest, Jest, etc., usually obvious from `package.json`).

If tests = yes, the agent should also ask: *"What's your testing convention — render-and-assert basics, full a11y / kbd tests, snapshot, none-of-the-above?"* — to avoid generating useless or contradictory tests.

---

## Recap before Act III

After answering, recap in one paragraph:

> *"Got it. I'll generate components at `src/shared/ui/<kebab>/<kebab>.tsx + index.ts`, import them with `@shared/ui/...`, use Tailwind extending your existing config, compose classes with `cn` from `@shared/utils/cn`, named exports, install fonts via `@fontsource` (with your confirmation before running `pnpm add`), and skip tests. Sound right?"*

Wait for confirmation before producing the **component plan** in Act III.
