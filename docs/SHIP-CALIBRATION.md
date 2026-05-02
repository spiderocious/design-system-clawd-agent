# Ship · calibration

How to read an existing target repo *before* asking any questions, so the discovery script becomes a confirmation pass instead of a blank questionnaire.

The agent is **read-only** during calibration. No writes. No installs. No formatting.

---

## What to read

In this exact order. Stop reading once you have an answer for each question — don't open more files than needed.

### 1 · `package.json`

The single most informative file. Capture:

- **React (or framework) version** — `dependencies.react` / `dependencies.next` / `dependencies.@remix-run/*` / `dependencies.solid-js` / `dependencies.svelte`
- **Styling deps** — presence of any of:
  - `tailwindcss` → Tailwind
  - `@vanilla-extract/css` → vanilla-extract
  - `styled-components` → styled-components
  - `@emotion/react` → Emotion
  - `*.module.css` files in `src/` → CSS Modules (no dep, but visible by glob)
  - **None of the above** → either unstyled headless or vanilla CSS
- **Class-composition deps** — `clsx`, `tailwind-merge`, `classnames`, none
- **Font deps** — any `@fontsource/*` package
- **Test framework** — `vitest`, `jest`, `@testing-library/react`, `playwright` (component testing)
- **Type system** — `typescript` present? if so, `.tsx`. If not, `.jsx`.

### 2 · `tsconfig.json` and `tsconfig.app.json`

For the alias map. Look at `compilerOptions.paths`:

```json
"paths": {
  "@shared/*": ["src/shared/*"],
  "@/*": ["src/*"]
}
```

Capture the most-common alias used elsewhere in the codebase (see step 4). Don't pick the first one in the list — pick the one that matches the components folder.

### 3 · `vite.config.ts` / `next.config.*` / `webpack.config.*`

Confirm the alias is also wired in the bundler (TypeScript paths alone aren't enough). For Vite, look for `resolve.alias`:

```ts
resolve: {
  alias: { '@shared': path.resolve(__dirname, './src/shared') }
}
```

If the bundler config doesn't match the tsconfig paths, **flag this as a finding** — the user may have intended both to match. Don't fix it; just report.

### 4 · One existing component (if any)

Find one with:

```
find src -type f \( -name '*.tsx' -o -name '*.jsx' \) -path '*ui*' | head -3
```

Or whatever the component path looks like. Read **one** file. Capture:

- **forwardRef vs not** — does it `forwardRef<HTMLButtonElement, ButtonProps>`?
- **Export style** — `export const X = ...` (named) vs `export default X` (default) vs both
- **File-and-folder layout** — is there an `index.ts` next to the component file? does the folder name match the component (kebab-case)?
- **Class-composition import** — where does `cn` (or whatever) come from? (`@shared/utils/cn`, `~/lib/utils`, etc.)
- **Class string style** — single-line, multi-line with `cn(`, raw template literal? Capture the *shape* so generated components match.
- **JSDoc style** — does the file have a JSDoc block referencing source HTML/CSS? if so, mirror that. (Medcord's button does — a template worth copying.)
- **Type imports** — `import { type ButtonHTMLAttributes }` vs `import type { ButtonHTMLAttributes }` vs `React.ButtonHTMLAttributes` style
- **Prop interface vs type** — does the file use `interface ButtonProps` or `type ButtonProps`?

### 5 · `tailwind.config.*` (only if Tailwind detected)

Read the whole file. Capture:

- Is `theme.extend` used (good — preserve the user's customizations)?
- Does the existing config read CSS variables (`'var(--…)'` strings)?
- Is the content glob covering where the components are going to live?
- Are there custom fonts, colors, radii already? → the new tokens need to **merge in**, not replace.

### 6 · `globals.css` / `app.css` / `index.css` / `src/styles/*`

Find the file with `@tailwind base / components / utilities` directives. That's the global stylesheet. Read it for:

- Existing CSS-var tokens (`:root { --primary: ... }`) that might collide with the Studio's tokens
- `@layer base` rules
- Font-face declarations
- Global resets

### 7 · `*.test.*` next to components?

```
find src -type f -name '*.test.*' -path '*ui*' | head -1
```

If yes → tests-next-to-components is the convention. Default Q8 to "yes."
If no → tests live elsewhere (e.g. a separate `tests/` folder or no tests). Default Q8 to "no."

### 8 · Pre-commit hooks (Husky / lint-staged)

Check `package.json` `"husky"` field, `.husky/`, or `lint-staged` config. Capture if pre-commit runs:

- ESLint (so generated files must lint cleanly)
- Prettier (so generated files must be formatted)
- Type-check (so generated files must compile)

This matters because **generated files have to pass the user's pipeline.** If pre-commit auto-fixes formatting, write to the user's prettier config; don't fight it. If pre-commit blocks ESLint warnings (max-warnings 0), be careful with unused imports in generated files.

---

## Reporting back

After all of the above, write the calibration report as one paragraph + one short list. Format:

> **Calibration report — `<target-repo-name>`**
>
> React 18.3, TypeScript, Vite. Tailwind 3.4 with a customized config that already reads CSS-var tokens — your foundation tokens will fit. Components live at `src/shared/ui/<kebab>/<kebab>.tsx + index.ts`, alias `@shared/*` (matched in both tsconfig and vite). The existing `Button` uses `forwardRef`, named exports, and imports `cn` from `@shared/utils/cn`. JSDoc references source HTML + CSS line ranges (I'll mirror that). No tests next to components — they live in `tests/` (default ship: skip tests). Pre-commit runs ESLint with max-warnings 0 and Prettier — generated files will conform.
>
> One finding to flag:
> — `vite.config.ts` doesn't declare the `@shared` alias even though `tsconfig.app.json` does. This works in IDE but may break in builds if anything outside the IDE resolution path imports through it. (Not blocking; just noting.)
>
> Confirm or correct, and I'll move to discovery.

---

## When calibration finds **conflicts**

Surface them, don't fix them.

Examples:

- **Mixed file-layout conventions.** Some components are `Button.tsx`, others are `card/card.tsx + index.ts`. → Ask the user which to follow for new ones.
- **Multiple class-composition utils.** `cn` exists at one path, `clsx` is also imported elsewhere. → Ask which to use; default to whichever is more recent / better-written.
- **Tailwind config customizations that collide with Studio tokens.** E.g. existing `colors.green` is a different ramp than the Studio's `green`. → Ask: *"Your existing `green` ramp is a different palette. Do you want me to (a) namespace mine as `colors.studio-green`, (b) replace yours, (c) extend yours and override only the specific shades the design uses?"* Default to **(a)** to be safe.
- **Aliases declared but not used.** tsconfig has `@shared/*` but every component does `../../shared/...`. → Note it; ask if the new components should use the alias or follow the existing relative-import convention.

---

## When calibration finds **nothing** (empty / fresh repo)

Skip ahead to discovery. Note in the report: *"This looks like a fresh React project — no existing components, no styling system installed yet. The discovery questions will set the conventions from scratch."*

In that case, `Q4 — styling` defaults to **Tailwind** (lightest, closest to Studio HTML), `Q3 — layout` to **folder-per-component**, `Q6 — exports` to **named**, `Q7 — fonts` to **@fontsource**.

---

## What never to do during calibration

- Never run `pnpm install`, `npm install`, or any package manager command
- Never run a formatter or linter
- Never modify any file in the target repo
- Never assume a convention from a single file — read at least 1–2 components if available before declaring "this is the convention"
- Never report findings the user didn't ask for (no "I notice your ESLint config is outdated" — that's not your job here)
