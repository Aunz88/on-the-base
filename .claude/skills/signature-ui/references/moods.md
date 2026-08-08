# Moods — the skin catalogue

A **Mood** is the dress over the skeleton: a paper tone, an accent hue, and a type personality.
Pick one named mood per build. The rule that keeps pages from converging: **consecutive moods
must differ on at least one axis** —

- **Paper band** — dark (L < 30%) · mid (30–85%) · light (> 85%)
- **Accent hue** — warm (10–60°) · cool (200–300°) · neutral · other (green/phosphor/etc.)
- **Display personality** — high-contrast serif · humanist serif · grotesk · geometric sans ·
  mono · display/condensed

All colours below are given as OKLCH so lightness stays perceptually even. Fonts are free
(Google Fonts / open licences) so the skill never depends on a paid asset.

## Named moods

| Mood | Paper | Accent | Display / Body | Feels like |
| --- | --- | --- | --- | --- |
| **Ink** | light `oklch(98% 0.005 95)` | near-black `oklch(20% 0.02 260)` | Fraunces / Inter | classic editorial, print-quiet |
| **Bone** | warm off-white `oklch(96% 0.012 80)` | terracotta `oklch(62% 0.14 40)` | Spectral / Work Sans | warm, human, considered |
| **Slate** | cool grey `oklch(95% 0.006 250)` | cobalt `oklch(55% 0.16 255)` | Space Grotesk / Inter | modern SaaS, calm-technical |
| **Midnight** | near-black `oklch(18% 0.02 265)` | electric `oklch(72% 0.17 200)` | Sora / Inter | atmospheric, product-launch |
| **Terminal** | black `oklch(15% 0.01 150)` | phosphor `oklch(80% 0.19 150)` | JetBrains Mono only | developer tool, intentional mono |
| **Botanical** | pale sage `oklch(96% 0.02 140)` | forest `oklch(48% 0.10 150)` | Newsreader / Karla | organic, editorial-green |
| **Press** | paper white `oklch(97% 0.004 90)` | signal red `oklch(56% 0.20 27)` | Libre Franklin / Lora | newsprint, urgent, opinionated |
| **Sand** | tan `oklch(93% 0.03 75)` | clay `oklch(52% 0.09 55)` | Fraunces / Karla | soft luxury, warm minimal |
| **Dusk** | deep plum `oklch(25% 0.05 320)` | amber `oklch(78% 0.15 70)` | Clash Display / Inter | moody, expressive, brand-led |
| **Blueprint** | cool paper `oklch(96% 0.01 240)` | ink-blue `oklch(45% 0.12 250)` | IBM Plex Sans / IBM Plex Mono | precise, engineering, drawn |

Reach past the top of the list. The first mood you think of is usually the one everyone reaches
for — deliberately scan for one that differs from your last build on an axis above.

## Genre → mood shortlist

If the brief has an obvious genre, rotate within its cluster (keeps variety while staying on
tone):

- **AI / media / atmospheric** → Midnight · Terminal · Dusk
- **SaaS / developer / infra** → Slate · Blueprint · Terminal
- **Editorial / content / brand** → Ink · Press · Botanical
- **Consumer / warm / lifestyle** → Bone · Sand · Botanical

## Custom mood

Build a custom mood — don't pick from the catalogue — when the brief:

- names a specific brand colour ("our terracotta is #c0392b"),
- describes a multi-word aesthetic (3+ vibe words mapping to a specific feel), or
- attaches a swatch / moodboard / Pantone chip.

To construct one:

1. **Anchor the accent.** Convert the brand colour to OKLCH. If none given, choose a hue that
   fits the vibe and set chroma modestly (0.08–0.18 — high chroma reads cheap fast).
2. **Set the paper.** Pick a band (dark/mid/light) that fits the tone, tinted a few points toward
   the accent hue so paper and accent feel related, not bolted together.
3. **Derive a ramp.** Generate 5–7 steps between paper and ink at even lightness intervals for
   surfaces, borders, and muted text. Keep hue roughly constant along the ramp.
4. **Pair the type.** One distinctive display face + one highly legible body face, both free-
   licensed. Contrast their personalities (a serif display over a grotesk body, or vice-versa) —
   two similar sans-serifs read as one boring font.
5. **Record the three axes** in the stamp so future builds can differ from it:
   `mood: custom · paper <band> · accent <hue> · display <style>`.

Every Slop Check gate still applies to a custom mood — bespoke is not an excuse for slop.
