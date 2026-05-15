# UI Translation Guide — HTML Spec → React Component Library

> **What this is:** A briefing for any AI agent (or developer) tasked with turning a finished HTML design spec into a production React component library. It is framework-agnostic in principle; the examples throughout use Medcord as the reference project. Where Medcord specifics appear, they are clearly labelled.
>
> **How to use it:** Read sections 1–3 before touching any code. Use sections 4–9 while building. Use sections 10–11 to verify before handing off.

---

## 1. Understand the three artefacts

Every project of this kind has three things. Know which is which before you start:

| Artefact | What it is | Who owns it |
|---|---|---|
| **HTML spec** | Figma-exported (or hand-written) HTML files + a foundation CSS file. These are the visual source of truth. Never edit them. | Designer |
| **Component library** | React (or Vue, Svelte, etc.) components that implement what the spec shows. This is what you build. | Engineer |
| **Viewer / storybook** | A standalone app or route in an existing file that renders the library live. The designer reviews work here. | Engineer |

These are siblings. The HTML spec survives as the canonical reference; your output is its production sibling, not its replacement.

**Medcord example:**
- HTML spec: `/Users/feranmi/codebases/2026/medcord-revamp/Medcord Design System/`
- Component library + viewer: `/Users/feranmi/codebases/2026/medcord-app/apps/design-system/`

---

## 2. Ask these questions before writing a single line

Run through this list every session. Most have a detectable default — calibrate from the repo first, then ask only what you couldn't determine.

### 2.1 About the spec

1. **Where is the HTML spec folder?** (The folder containing the `.html` files and `_foundation.css`)
2. **Where is the foundation / token file?** (Usually `_foundation.css` or `tokens.css` — the file that defines all the CSS custom properties)
3. **Are there multiple HTML files (one per component group) or one big file?**

If given enough context, you might not need to ask all these, you can read the files given directly, but confirm your assumptions/conclusions from the file structure with the user before proceeding.

### 2.2 About the target

4. **What framework?** React / Vue / Svelte / Solid — and what version?
5. **What styling system?** Tailwind / CSS Modules / vanilla-extract / styled-components / unstyled
6. **Where does the library output land?** (Path, and any path aliases in `tsconfig`/`vite.config`)
7. **Is there a viewer app?** If yes, where? If no, should one be created? If it should be a part of an existing app where should the route be added?

### 2.3 About scope

8. **Is mobile responsiveness required?** Default: yes unless told otherwise.
9. **Is dark mode required?** Default: NO!
10. **Should I run lint and typecheck after each batch?** Default: yes. Always before reporting done.
11. **Are there existing components to match conventions against?** If yes, read one before writing anything.
12. **Should I write tests?** Default: no, unless the project already has tests or the user explicitly asks for them.

---

## 3. Calibrate the target repo before writing

If the target repo already has code, read it before writing anything. You are looking for:

- **File layout** — folder-per-component? single file? barrel `index.ts`?
- **Export style** — named exports or default exports?
- **Class composition** — is there a `cn`/`clsx` helper? Where is it imported from?
- **Prop convention** — `readonly` interfaces? `interface` or `type`? `forwardRef` or not?
- **Null guard style** — `!= null` or `!== null && !== undefined` or `?? fallback`?
- **TypeScript strictness** — `noUncheckedIndexedAccess`? `strictNullChecks`?
- **Comments** — do existing components have docstrings? inline comments?

Write one short paragraph reporting what you found. Example:

> *"React 19, Tailwind v3 reading CSS-var tokens, alias `@ui/*` → `src/ui/`, components at `src/ui/<kebab>/<kebab>.tsx + index.ts`, named exports only, no forwardRef, readonly props, no cn utility — class arrays joined with `.join(' ')`, eqeqeq always enforced."*

Then match those conventions in everything you write. **The repo's conventions win over your preferences.**

---

## 4. Read the HTML spec

For each HTML file in the spec:

1. **Identify every visual state** — default, hover, focus, active, loading, error, disabled, empty, selected
2. **Identify every prop axis** — size (sm/md/lg), variant (primary/secondary/quiet), icon position (left/right/only), etc.
3. **Identify CSS custom properties used** — `var(--surface-raised)`, `var(--text-primary)`, etc. Map them to your project's token file
4. **Note bespoke pixel values** — `font-size: 13px`, `padding: 14px 18px` → these become inline arbitrary Tailwind values or CSS variables
5. **Identify what is a component vs what is a scene** — a button is a component; a full page layout showing three buttons in context is a scene. Build the component; record the scene as a demo in the viewer. Don't ship scenes as library exports.

### Token categories to look for

Foundation CSS files almost always define tokens in these categories. Identify the naming convention used in *your* spec:

```
Surface / background tokens     (page bg, card, input, sunken)
Text tokens                     (primary, secondary, tertiary, disabled)
Border tokens                   (default, subtle, focus)
Brand / accent tokens           (50–900 scale)
Semantic status tokens          (danger, warning, success, info)
  — each with: icon, bg, surface, border sub-tokens
Neutral / white                 (for text-on-dark)
```

**Medcord token examples** (for reference — your spec will use different names):
```css
--surface-canvas / --surface-raised / --surface-sunken / --surface-base
--text-primary / --text-secondary / --text-tertiary / --text-disabled
--border-default / --border-subtle / --border-focus
--brand-50 … --brand-700
--danger-icon / --danger-bg / --danger-surface / --danger-border
--warning-icon / --warning-bg / --warning-surface / --warning-border
--records-50 … --records-800   (green / clinical ok)
--patient-50 … --patient-700   (blue / patient identity)
--neutral-0                    (white)
```

Dark mode: look for a `[data-theme="dark"]` or `.dark` selector block in the foundation CSS that redefines the same properties. If it exists, components should consume tokens only — they never branch on dark mode themselves.

---

## 5. Component conventions (detect, then match)

### 5.1 File layout

Detect from existing code. If building from scratch, prefer:

```
src/ui/<kebab-name>/
├── <kebab-name>.tsx     ← all component code for this group
└── index.ts             ← named re-exports only
```

### 5.2 TypeScript

Standard strict-mode patterns:

```tsx
// Props: readonly fields, explicit types
export interface ButtonProps {
  readonly variant?: 'primary' | 'secondary';
  readonly children: React.ReactNode;
  readonly onClick?: () => void;
}

// Array access under noUncheckedIndexedAccess
const item = arr[0];                    // type: T | undefined
const item = arr[0] ?? defaultValue;    // ✓ safe

// Null guards — match what the project uses
// Option A (eqeqeq: always)
{value !== null && value !== undefined && <span>{value}</span>}

// Option B (eqeqeq with null exception allowed)
{value != null && <span>{value}</span>}

// Option C (nullish coalescing — preferred when you just need a fallback)
<span>{value ?? 'Default'}</span>
```

Detect which pattern is in use from existing code and match it exactly.

### 5.3 Styling (Tailwind)

```tsx
// Arbitrary values for bespoke pixel values from the spec
<div className="text-[13px] px-[22px] h-[132px]" />

// Token consumption
<div className="text-[var(--text-primary)] bg-[var(--surface-raised)]" />

// Class composition — detect whether project uses cn/clsx or .join()
// If cn exists:
className={cn('base-classes', condition && 'conditional-class', className)}

// If no cn (join pattern):
className={['base-classes', condition ? 'active' : '', className].join(' ')}

// Inline style only when Tailwind genuinely can't express it:
// repeating-linear-gradient, dynamic CSS vars, SVG props, grid-template-columns with many values
style={{ gridTemplateColumns: '1fr auto 120px' }}
```

### 5.4 Mapping HTML → React

| HTML pattern | React / Tailwind equivalent |
|---|---|
| `style="color: var(--text-primary)"` | `text-[var(--text-primary)]` Tailwind class |
| `font-size: 13px` | `text-[13px]` |
| `padding: 14px 18px` | `px-[18px] py-[14px]` |
| `grid-template-columns: 1fr auto` | `style={{ gridTemplateColumns: '1fr auto' }}` |
| `display: none` conditionally | `{condition && <Element />}` |
| `class="a b c"` with conditional | `['a', condition ? 'b' : ''].join(' ')` or `cn(...)` |
| `repeating-linear-gradient(...)` | `style={{ background: 'repeating-linear-gradient(...)' }}` |
| `opacity: 0.85` | `opacity-[0.85]` or `style={{ opacity: 0.85 }}` |

### 5.5 Icons

Detect the project's icon library. Common patterns:

```tsx
// lucide-react (most common)
import { ChevronRight, X, Search } from 'lucide-react';
// or via an alias:
import { ChevronRight, X } from '@icons';

// Use the size prop, not width/height:
<ChevronRight size={14} />
```

---

## 6. The viewer app

### 6.1 Purpose

The viewer is a standalone app that renders every component in every state. The designer reviews here — not in Figma, not in a PR. Keep it current.

Each component group gets one route. Each route gets a screen file that shows:
- The primary real-world use case first (contextual scene)
- Then variants, sizes, states (in a component row grid)
- Then edge cases

### 6.2 Wiring a new route (Medcord pattern — adapt to your project)

In Medcord the viewer is a React Router app with lazy-loaded routes. The pattern:

**1. Add the route constant**
```ts
// src/shared/routes.ts
export const ROUTES = {
  MY_FEATURE: '/my-feature',
} as const;
```

**2. Add the nav item**
```ts
// src/shared/nav-items.ts
{ label: 'My Feature', route: ROUTES.MY_FEATURE, group: 'Primitives' },
// groups: 'Foundation' | 'Primitives' | 'Display' | 'Containers' | 'Navigation & Feedback' | 'Domain'
```

**3. Register the lazy route**
```tsx
// src/app.routes.tsx
const MyFeatureScreen = lazy(() =>
  import('@features/my-feature/my-feature-screen').then((m) => ({ default: m.MyFeatureScreen })),
);
// inside routes array:
{ path: ROUTES.MY_FEATURE, element: <Lazy><MyFeatureScreen /></Lazy> },
```

**4. Create the screen**
```tsx
// src/features/my-feature/my-feature-screen.tsx
import { Section, ComponentRow } from '@features/shell/parts/preview-canvas';
import { MyComponent } from '@ui/my-feature';

export function MyFeatureScreen() {
  return (
    <div>
      <Section title="Primary use" description="When and why to use this.">
        <ComponentRow label="Default">
          <MyComponent />
        </ComponentRow>
      </Section>
    </div>
  );
}
```

If your project uses a different routing system (Next.js pages, TanStack Router, etc.), the concept is the same — adapt the mechanics.

### 6.3 Imperative services (DrawerService pattern)

For toasts and modals that need to be triggered imperatively (not via component tree state), the pattern is:

1. A **backing store** — a plain class with `subscribe(listener)` / `getState()` / mutation methods. No framework dependency.
2. A **service singleton** — exports bound method references. Call it from anywhere.
3. **Host components** — `<ModalHost />` and `<ToastHost />` mounted once at the app root. They use `useSyncExternalStore` to subscribe to the store and render via `createPortal`.

```ts
// Imperative call from anywhere — no props, no context
DrawerService.toast('Saved.', { type: 'success' });
DrawerService.showConfirmationModal('Delete record?', 'This is permanent.', {
  destructive: true,
  onConfirm: () => { /* ... */ },
});
```

**Medcord implementation:** `src/ui/drawer/` — `drawer-store.ts`, `drawer-service.ts`, `modal-host.tsx`, `toast-host.tsx`. Demo at `/drawer`.

---

## 7. Running checks

Adapt commands to your package manager and build tool. The pattern:

```bash
# TypeScript — must exit 0 before calling anything done
pnpm nx typecheck <project>        # Nx monorepo
npx tsc -b --noEmit                # plain Vite
npx tsc --noEmit                   # plain TS project

# Lint
pnpm nx lint <project>
npx eslint src/

# Build (smoke-test the bundle)
pnpm nx build <project>
npx vite build

# Dev server
pnpm nx serve <project>            # Nx
npx vite                           # plain Vite
```

**When to run:** After every batch of 3–5 components. Always before reporting a session complete.

**Common errors to expect:**

| Error | Cause | Fix |
|---|---|---|
| `Type 'T \| undefined' not assignable to 'T'` | `noUncheckedIndexedAccess` — array access | Guard with `?? fallback` or `if (x !== undefined)` |
| `eqeqeq` lint error | `!= null` or `== null` | Replace with `!== null && x !== undefined` or `=== null \|\| x === undefined` |
| `no-unused-vars` | State setter only used in JSX | Extract a named handler function |
| `Cannot find module '@icons'` | Path alias not in tsconfig | Add alias to both `vite.config.ts` and `tsconfig.app.json` |

---

## 8. Shipping components to a different app

When the user wants to move built components out of the viewer and into a product app:

1. **Calibrate** the target app (section 3 — read before writing)
2. **Tokens first** — copy or merge the CSS custom property definitions into the target's global stylesheet. Show a diff if the file already exists.
3. **Tailwind config** — if the target uses Tailwind, extend (never overwrite) their `tailwind.config.ts` to reference the CSS vars. Show the diff, wait for confirmation.
4. **Components** — adapt to the target's conventions, not the design system viewer's. If they use `cn`, use their `cn`. If they default-export, default-export.
5. **Don't ship scenes** — complex page-level layouts (a full EMR chart view, a bed board, a registration flow) are not library components. Record them in the migration report as "visual specs — build in the app, not the library."
6. **Write a migration report** — components generated, components skipped (and why), conventions detected, manual work remaining, path back to the HTML spec for visual reference.

---

## 9. Hard rules

- **Never write a file before you've shown a plan and the user has said "go"** — for net-new components. For bug fixes and typos, just fix.
- **Never overwrite an existing file without showing a diff first.** This applies to config files, global CSS, `package.json`, entry points.
- **Never run installs (`pnpm add`, `npm install`) without showing the exact command and waiting for confirmation.**
- **Never invent design.** If the HTML doesn't show a state, don't add one. If a prop shape is ambiguous, surface it in the plan — don't guess.
- **Never hardcode hex values.** Use CSS custom properties from the foundation file.
- **Don't fight the repo's conventions.** Their export style, class composition pattern, and null guard style win.
- **Don't ship scenes as components.** A button is a component. A patient list page is a scene.
- **No `console.log` in component code.**
- **Never skip git hooks** (`--no-verify`). Fix the root cause.

---

## 10. Session handoff checklist

Before ending a session or reporting done:

- [ ] Typecheck exits 0
- [ ] Lint passes (or all new violations are explicitly noted and deferred)
- [ ] Every new component has a matching `index.ts` export
- [ ] New routes are wired in routes config + nav config + route registry
- [ ] Dark mode tested (toggle in the viewer, or manually set `data-theme="dark"`)
- [ ] Mobile layout tested at the smallest breakpoint — nothing clips or overflows
- [ ] If a `DrawerService`-style singleton was added: `<ModalHost />` + `<ToastHost />` mounted at app root
- [ ] Any imperative service has a demo screen showing the full API surface

---

## 11. Reference: Medcord project specifics

> These are the concrete details for the Medcord design system. Treat this section as a worked example of the patterns above, not as universal rules.

**Repo:** `/Users/feranmi/codebases/2026/medcord-app/`
**Viewer:** `apps/design-system/` — Vite + React 19 + TypeScript strict + Tailwind v3
**HTML spec:** `/Users/feranmi/codebases/2026/medcord-revamp/Medcord Design System/`
**Dev port:** 5175

**Path aliases:**
| Alias | Resolves to |
|---|---|
| `@ui/*` | `src/ui/*` |
| `@features/*` | `src/features/*` |
| `@shared/*` | `src/shared/*` |
| `@icons` | `src/shared/icons/index.ts` (re-exports all of `lucide-react`) |

**Conventions detected:**
- No `forwardRef`, named exports only, no default exports
- `readonly` on every prop field
- No `cn`/`clsx` — class arrays joined with `.join(' ')`
- `eqeqeq: ['error', 'always']` — `!= null` is a lint error everywhere
- `noUncheckedIndexedAccess` — `arr[i]` returns `T | undefined`
- Icons: `import { X, ChevronRight } from '@icons'` with `size={n}` prop
- Inline `style={{}}` only for `repeating-linear-gradient`, dynamic props, SVG, multi-column grid values

**ESLint eqeqeq status:** ~120+ pre-existing `!= null` / `== null` occurrences across `src/ui/` and `src/features/`. Fix opportunistically in files you touch; full sweep only if asked.

**Key components:**
| Component | Import path | Notes |
|---|---|---|
| `Button`, `SplitButton`, `IrreversibleButton` | `@ui/button` | Variants: primary, secondary, quiet. States: loading, confirmed, disabled |
| `Modal`, `TypedConfirmModal`, `TwoPersonModal`, `SessionTimeoutModal`, `BreakTheGlassModal` | `@ui/modal` | `createPortal` to `document.body` |
| `Toast`, `InlineAlert`, `PageBanner`, `ContextMenu` | `@ui/feedback` | |
| `DrawerService` | `@ui/drawer` | Imperative singleton. `ModalHost` + `ToastHost` already in `ShellScreen`. Demo at `/drawer` |
| `TimeDrum` | `@ui/datetime` | Scroll wheel + up/down arrows. Clicking the time display toggles picker open/closed |
| `BodyDiagram` | `@ui/specialized` | SVG body map. Props: `markings`, `onMark`, `onMarkingsChange`, `allowFullView`. Drag to move, click to select/edit |
| `MarkdownEditor` | `@ui/specialized` | Working toolbar: bold, italic, heading, list, code, link. Shortcuts: ⌘B, ⌘I, ⌘K |
| `MarkdownViewer` | `@ui/specialized` | `react-markdown` renderer. Serif body, mono code |

**Nav groups (sidebar):** `'Foundation'` · `'Primitives'` · `'Display'` · `'Containers'` · `'Navigation & Feedback'` · `'Domain'`

**Decisions log:**
| Decision | Reason |
|---|---|
| No `cn`/`clsx` | Zero extra deps; `.join(' ')` is readable at this scale |
| `DrawerService` uses native pub-sub, not Zustand | No extra dep; `useSyncExternalStore` handles reactivity |
| `eqeqeq: always` with no null exception | Explicit nullish handling; caught real bugs during refactor |
| `react-markdown` for `MarkdownViewer` | Avoids hand-rolling a parser |
| SVG body diagram landmarks at 4.2px font | Density without crowding in the 100×220 viewBox |
| `TimeDrum` uses `passive: false` wheel listener | Must call `preventDefault()` to stop page scroll inside drum |
| `BodyDiagram` drag via pointer capture | Stays accurate when pointer leaves the SVG mid-drag |
| Mobile sidebar as a fixed drawer overlay | `hidden sm:flex` desktop + `fixed inset-y-0` mobile drawer |
