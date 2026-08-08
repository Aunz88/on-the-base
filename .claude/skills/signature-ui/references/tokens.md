# Tokens — the build ruleset

Everything visible references a **named token**. The reason isn't bureaucracy: named tokens are
what make a design a *system* instead of a pile of one-off values. They let a mood be swapped,
a build be audited, and a page stay consistent across a hundred components. Inline hex scattered
through rules is the opposite — every value is a decision no one can revisit.

Emit a `tokens.css` next to the page CSS containing every token used. Page rules reference tokens
by name and never inline a raw value.

## Colour

- **Declare everything in OKLCH** at `:root`. OKLCH keeps lightness perceptually even across
  hues, so a ramp actually looks evenly stepped. `oklch(L% C H)` — L 0–100%, C ~0–0.37, H 0–360.
- Name by **role, not value**: `--color-bg`, `--color-surface`, `--color-text`,
  `--color-muted`, `--color-border`, `--color-accent`, `--color-accent-contrast`. A component
  that says `var(--color-accent)` survives a mood change; one that says `#5b6cff` doesn't.
- Provide **states** for the accent: `--color-accent`, `--color-accent-hover`,
  `--color-accent-active`. Derive them by nudging L a few points, not by picking unrelated hues.
- **Contrast is a floor, not a goal.** Body text ≥ 4.5:1 against its background; large text and
  UI ≥ 3:1. Check the actual pairs you ship, especially muted text on tinted surfaces.

```css
:root {
  --color-bg: oklch(98% 0.005 95);
  --color-surface: oklch(96% 0.008 95);
  --color-text: oklch(22% 0.02 260);
  --color-muted: oklch(52% 0.02 260);
  --color-border: oklch(88% 0.01 260);
  --color-accent: oklch(55% 0.16 255);
  --color-accent-hover: oklch(50% 0.16 255);
  --color-accent-contrast: oklch(99% 0 0);
}
```

## Type

- **A modular scale, not random pixels.** Pick a ratio (1.2 minor third for calm, 1.25–1.333 for
  more drama) and step from a base. Name the steps: `--text-xs … --text-4xl`, `--text-display`.
  Random `font-size: 17px / 23px / 31px` is a tell that no system exists.
- Use `clamp()` for display sizes so they scale between mobile and desktop without a dozen
  breakpoints: `--text-display: clamp(2.5rem, 6vw, 5rem)`.
- **One display face + one body face.** Contrast their personalities. Single-font is allowed only
  when it *is* the design (an intentional mono terminal look) — not by accident.
- **Match headline size to headline length.** A 3-word hero can be huge; a 14-word hero at the
  same size wraps into a mess. Aim ≤ 7 words in the display headline and step the size down as
  length grows.
- No italic headings — italics survive for emphasis inside running body copy only. For heading
  emphasis use weight, an accent colour, or scale.
- Set `font-variant-numeric: tabular-nums` anywhere numbers align in columns (tables, pricing).

## Spacing & layout

- **A 4pt (or 8pt) scale** with semantic names: `--space-2xs: 4px … --space-2xl: 96px`. Every
  margin and gap references one. Arbitrary spacing is how rhythm dies.
- Grids use `minmax(0, 1fr)` for flexible columns so a long word can't blow the track out and
  force horizontal scroll.
- Wrap long/unbreakable strings: `overflow-wrap: anywhere` on content that can contain URLs,
  code, or long tokens.
- Establish one **focal point per viewport**. If everything is bold, nothing is — pick what
  leads and let the rest support it.

## Motion

- **Animate `transform` and `opacity` only.** Animating layout properties (width, height, top,
  margin) forces reflow and jank. Transform/opacity are cheap and smooth.
- **Three named easings**, no more: `--ease-out`, `--ease-in`, `--ease-in-out`. Avoid the browser
  default `ease` and avoid bounce/overshoot on UI state changes — it reads as a toy.
- **Honour `prefers-reduced-motion: reduce`.** Collapse spatial motion to a ≤150ms opacity
  crossfade. Some users get motion-sick; this is accessibility, not polish.
- **Cut before you add.** Remove any animation whose absence loses the user no information. Most
  pages need far less motion than they ship with.

## States

Every interactive element carries the full set — **default · hover · focus · active · disabled ·
loading · error · success** — because a button with only a hover state falls apart the moment a
real user tabs to it or a request is in flight.

- `:focus-visible` shows a **visible ring at ≥ 3:1 contrast**, appearing instantly (never
  animate the ring in — a keyboard user needs it *now*).
- Prefer *silent success* and *optimistic update + Undo* over celebratory toasts and confirm
  dialogs. Delay hover tooltips ~800ms; show focus tooltips at 0ms.

## Output hygiene

- **Append, don't clobber.** When a global stylesheet exists (`globals.css`, `index.css`), add
  your `:root` block and rules below its existing `@import` / `@tailwind` lines and reuse the
  project's own token names where they exist. Overwrite only if the user explicitly asks.
- **Stamp the CSS.** First non-empty line:
  `/* signature-ui · direction: <name> · mood: <name> · accent-hue: <hue> */`
- Always emit `tokens.css`, even for a single-page build — it's what makes the design portable.
