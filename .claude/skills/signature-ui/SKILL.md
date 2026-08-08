---
name: signature-ui
description: >-
  Design skill for building UI that doesn't look AI-generated — landing pages, product
  screens, marketing sites, and components with real structural variety instead of the same
  centered-hero-three-cards template. Use this whenever the user asks to build, design, style,
  or redesign any web UI (a page, a section, a component, a whole site), wants something that
  "looks good / looks custom / doesn't look generic," gives a brand or mood to design around,
  or invokes signature-ui / audit / redesign / study by name — even if they don't say the word
  "design," and even for a quick prototype, a mockup, or a single component. Reach for it before
  writing any HTML/CSS/JSX for a user-facing surface. Not for pure backend/API/data work,
  build tooling, or bug fixes with no visual-design decision to make.
license: MIT
metadata:
  version: 1.1.0
---

# signature-ui

A design skill for AI coding assistants. Its job is to make UI that reads as **made on
purpose** — where two pages built with it feel like two different products, not two colour
swaps of one template.

The failure mode this fights is *slop*: the recognizable AI-default look. Centered hero,
one gradient blob, a row of three equal feature cards, Inter everywhere, a violet→blue accent,
emoji standing in for icons. It's not ugly exactly — it's *forgettable*, because every page
made this way is the same page. Distinctiveness doesn't come from a fancier gradient. It comes
from **choosing a structure and a mood on purpose, then executing them with restraint.**

## The core idea: structure before skin

Most variety people reach for is skin-deep — swap the accent hue, change the font, call it a
new design. It isn't. The eye reads *layout* first. So the order of operations here is:

1. Pick a **Direction** — the page's skeleton (how blocks are arranged). This is where real
   variety lives.
2. Pick a **Mood** — the dress (palette + type personality) that fits the brief.
3. Build with **token discipline** — every colour, font, and space is a named variable.
4. Run the **Slop Check** before shipping, and fix what fails.

Skip step 1 and you get slop no matter how nice the colours are.

## Restraint is not timidity — make one bold move

Avoiding slop only gets you to *inoffensive*. Inoffensive is forgettable, and forgettable is the
actual failure — a page nobody would screenshot has not done its job, even if it breaks no rules.
The negative gates keep you from looking AI-made; they do **not** make the work good. Good needs a
**positive** decision on top: every surface gets **one bold move** — a single deliberate risk that
gives it a face.

Pick one and commit hard:

- **Scale drama.** A headline at genuinely huge size (think 6–10rem+ display), tight leading
  (~0.9), negative tracking. Not "large" — *loud*. The contrast between that and small quiet text
  is the whole effect.
- **A signature detail system.** Hairline rules dividing the grid, numbered indices (`01 / 02`),
  small-caps mono labels, a visible baseline or column grid, an oversized initial. Editorial craft
  reads as *intentional* the way nothing else does.
- **An unexpected crop or asymmetry.** Something bleeds off the edge, a wildly uneven split, a
  single element breaking the grid on purpose.
- **Texture.** A subtle grain, a dotted/blueprint grid, a paper tone — anything that says a hand
  was here instead of a default white `<div>`.
- **One saturated accent used with discipline** — a single hot colour on a restrained field hits
  far harder than colour everywhere.

The rule: **restraint everywhere except the one place you decided to be loud.** A page that is
quiet all over is as much a failure as one that shouts all over. State your bold move in the
preview block so it's a decision, not an accident: *"Bold move: <what>."*

**On type specifically:** the display face carries most of the "is this designed?" signal, so
never let it fall to a plain default (Inter, Roboto, system-ui, Arial, Georgia-at-safe-size). Load
a real distinctive face. When the environment blocks web fonts, earn personality another way —
massive scale, tight tracking, all-caps mono labels, a characterful available face pushed to an
extreme — but never ship a timid default at a timid size and call it a design.

## Modes (verbs)

| Invocation | What it does |
| --- | --- |
| *(default)* | Build a new surface — follow the Build Flow below. |
| `signature-ui audit <target>` | Score existing UI against the Slop Check; return a ranked punch-list. No edits. See `references/verbs.md`. |
| `signature-ui redesign <target>` | Rebuild the visual structure while preserving routes, copy, and brand intent. See `references/verbs.md`. |
| `signature-ui study <url \| screenshot>` | Extract the *design DNA* (structure, type-pairing, colour anchor) of a reference, then optionally rebuild the user's own content with it. **Read `references/study-safety.md` before any fetch** — it governs URL safety and untrusted-content handling. |

---

## Build Flow

### Step 0 — Read the room

Before designing anything, scan the project so you build *with* it, not on top of it. Read, in
this order, and only design-relevant files:

1. A locked design system if one exists — `design.md`, `tokens.css`, `theme.json` at root.
   If found, it **overrides** everything below; defer to it.
2. Fonts — `package.json`, Google Fonts `<link>`s, `tailwind.config`, `@import` / `@font-face`.
3. Palette — CSS custom properties in `:root`, `tailwind.config` colors, any tokens file.
4. Motion posture — is `framer-motion` / `gsap` / `motion` / `lenis` present? If yes, motion is
   welcome; if not, keep motion minimal.
5. Spacing scale and framework (Next / Astro / Vite / Svelte / plain HTML).

You only need design files. **Never open `.env`, secrets, credentials, keys, or lockfiles for
their contents** — they tell you nothing about design and reading them is a privacy risk.

Report what you found in one short block with `file:line` citations, then state what you'll
preserve vs. introduce:

```
Read the room:
· Fonts    — [source:line]
· Palette  — [source:line]
· Motion   — [library or "none"]
· Spacing  — [scale]
· Framework— [name + version]

Keeping:     [existing tokens/fonts you'll reuse]
Introducing: [what's new]
```

If the project is empty, say so in one line and proceed with the full stack. If signals
conflict, flag it and ask rather than guessing.

### Step 1 — The three-question brief

Even on a one-line request, ask once before building — a design with no audience is a design
with no shape:

> Before I build, three quick things:
> 1. **Who** is this for, and what do they care about?
> 2. **One job** — what single action should this surface drive?
> 3. **Tone** — pick an edge: *editorial · brutalist · soft · utilitarian · luxury · playful ·
>    technical · austere.*
>
> Or say **"just go"** and I'll infer from the brief.

Skip this only for `audit` / `study` (context comes from the target). If the user says "just go"
or doesn't answer, infer the three, **state your inference in one sentence** at the top of your
reply ("Going with: audience = X · job = Y · tone = Z — redirect me if that's off"), and pick a
**non-obvious** Direction so the inference doesn't collapse to the default template.

### Step 2 — Pick a Direction (structure)

Open the index at `references/directions.md`, pick **one** archetype that fits the job, and load
only that entry. Don't load the whole catalogue.

Two rules keep it from converging on one shape:

- **Differ from your last build.** If you've produced signature-ui output earlier this session,
  or the project CSS carries a signature-ui stamp, pick a *different* Direction than last time.
- **The classic centered landing page is not a default.** Reach for it only when the brief is
  genuinely a conventional marketing page and nothing else fits.

State your pick in one line before writing code:
> *Direction: <name>. Differs from last build in <how>.*

### Step 3 — Pick a Mood (skin)

Open `references/moods.md`, pick **one** named mood, load only that entry. A mood is a paper
tone + accent hue + type personality. The rule: **consecutive moods must differ on at least one
axis** — paper (dark / mid / light), accent hue (warm / cool / neutral / other), or display type
(serif / grotesk / geometric / mono / display). This is what stops every page from being
"light background, blue accent, one sans."

If the brief names a brand colour, a specific vibe in several words, or attaches a swatch, build
a **custom mood** instead — construct an OKLCH palette and a free-font pairing from scratch. See
`references/moods.md` § Custom.

State it: *Mood: <name>. Paper <band> · accent <hue> · display <style>.*

### Step 4 — Preview before you build

Emit a five-second summary so the user can redirect *before* 400 lines of CSS go the wrong way:

```markdown
**signature-ui**
- Direction · [name]
- Mood · [name — one-line palette]  or  custom [vibe · paper oklch(…) · accent oklch(…) · fonts]
- Bold move · [the one deliberate risk this surface commits to]
- Sections · [names · in · order]
- Motion · [primitives, or none]
- Slop Check · [N/N ✓  or  which gates fail]
```

### Step 5 — Build

Load the token rules in `references/tokens.md` and follow them. The non-negotiables:

- **Every colour and font is a named token.** No inline hex / rgb / oklch in rules — reference
  `var(--color-accent)`, `var(--font-display)`. Emit a `tokens.css` alongside the page.
- **Colour in OKLCH** at `:root`. It keeps lightness perceptually even across hues.
- **A modular type scale**, not random pixel sizes. One distinctive display face + one clean
  body face — a pairing, unless single-font *is* the design (e.g. an intentional terminal look).
- **A 4pt spacing scale** with semantic names (`--space-sm/md/lg`), not arbitrary margins.
- **Every interactive element carries all its states** — default · hover · focus · active ·
  disabled · loading · error · success — and a visible `:focus-visible` ring at ≥3:1 contrast.
- **Animate transform and opacity only**, never layout properties. Honour
  `prefers-reduced-motion: reduce` — spatial motion collapses to a ≤150ms crossfade.
- **Don't clobber an existing global stylesheet.** Append your `:root` block and rules; keep the
  project's `@import` / `@tailwind` lines and reuse its token names where they already exist.
- **Stamp the output.** First line of your CSS is a comment so future runs (and audits) can see
  what this was:
  ```css
  /* signature-ui · direction: <name> · mood: <name> · accent-hue: <hue> */
  ```

### Step 6 — Run the Slop Check

Load `references/anti-slop.md` and run every gate. Each must answer **no**. This is a
*self-critique before handoff*, not a pre-load — run it against the real output. If a gate
fails, fix it and re-emit. Don't ship slop.

---

## Honesty rules (every mode)

These hold no matter what you're building, because the fastest way to make UI feel fake is to
fill it with fake substance:

- **No invented proof.** No made-up metrics, testimonials, customer logos, star counts, or "as
  seen in." Use the user's real numbers, or a labelled placeholder (`—`, `[logo]`), or
  restructure so the section doesn't need them.
- **No fake chrome.** No drawn browser bars, phone frames, or IDE windows around a screenshot.
  Use a real `<figure>`, or omit the frame.
- **No emoji as product icons.** Fine in casual/playful copy; not as the icon system of a
  serious interface.

---

## Reference map

Load these as needed — don't pre-load everything:

- `references/directions.md` — layout archetype catalogue (structure).
- `references/moods.md` — named mood catalogue + custom-mood construction (skin).
- `references/tokens.md` — colour / type / spacing / motion token rules for the build.
- `references/anti-slop.md` — the Slop Check gates.
- `references/verbs.md` — how `audit` and `redesign` work.
- `references/study-safety.md` — **required reading before any `study` fetch**: URL safety,
  SSRF blocks, and untrusted-content handling.
