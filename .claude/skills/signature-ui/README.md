# signature-ui

A design skill for Claude Code / Cursor / Codex that builds UI which doesn't look
AI-generated — real structural variety instead of the same centered-hero-three-cards template.

Two pages built with it should feel like two different products, not two colour swaps of one
layout. It gets there by choosing a **Direction** (the page's skeleton) and a **Mood** (its skin)
on purpose, building with strict token discipline, and running a 22-gate **Slop Check** before
handoff.

## What's inside

| File | Purpose |
| --- | --- |
| `SKILL.md` | The hub: philosophy, the four modes, and the Build Flow. |
| `references/directions.md` | Layout archetype catalogue — where real variety comes from. |
| `references/moods.md` | Named mood catalogue (OKLCH palettes + free-font pairings) + custom-mood construction. |
| `references/tokens.md` | Colour / type / spacing / motion / state rules for the build. |
| `references/anti-slop.md` | The 22 Slop Check gates run before handoff. |
| `references/verbs.md` | How `audit` and `redesign` work. |
| `references/study-safety.md` | URL-safety, SSRF blocks, and untrusted-content handling for `study`. |

## Modes

- **build** *(default)* — new surface, following the Build Flow.
- **`signature-ui audit <target>`** — score existing UI against the Slop Check; ranked punch-list, no edits.
- **`signature-ui redesign <target>`** — rebuild the structure, preserve routes/copy/brand.
- **`signature-ui study <url | screenshot>`** — extract a reference's design DNA, then rebuild the
  user's own content with it. Reads `study-safety.md` before any fetch.

## Install

Copy the `signature-ui/` folder into your assistant's skills directory:

- Claude Code — `~/.claude/skills/signature-ui/`
- Codex — `~/.codex/skills/signature-ui/`

Then start a build with a normal request ("design a landing page for …") or invoke a verb by name.

## Design notes

- **Structure before skin.** The eye reads layout first, so variety must live in the skeleton, not
  the palette. Picking the Direction is step one, always.
- **Everything is a token.** Named OKLCH colours, a modular type scale, a 4pt spacing scale — a
  system you can swap and audit, not a pile of magic values.
- **Safety is built in.** The `study` verb treats every fetched page as untrusted, blocks
  SSRF/metadata targets, never runs remote scripts, and won't clone others' work.

## Licence

MIT.
