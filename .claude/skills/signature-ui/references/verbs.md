# Verbs — audit & redesign

The default mode builds a new surface. These two verbs work on something that already exists.
(`study` has its own file, `study-safety.md`, because it touches the network.)

---

## `signature-ui audit <target>`

Score existing UI against the Slop Check and hand back a ranked punch-list. **Read only — never
edit in audit mode.** The value is an honest diagnosis the user can act on.

1. Read the target (a file, a component, a route's CSS). If a signature-ui stamp is present, note
   the recorded Direction and Mood — an audit checks whether the build actually delivered them.
2. Run every gate in `references/anti-slop.md` against what's really there.
3. Return a **ranked** list — worst offenders first — with, for each finding:
   - the gate it fails and a one-line why,
   - the specific location (`file:line` or selector),
   - a concrete fix in one sentence.
4. End with a headline score (`N/22`) and the two or three changes that would most improve it.

Keep it specific and kind. "Gate 1: the page is a centered hero + 3 equal cards — try a Bento
Grid so the primary feature gets a larger tile (`sections.tsx:40`)" beats "layout is generic."
Don't pad the list with nitpicks; a short list of real problems is more useful than a long list
of trivia.

---

## `signature-ui redesign <target>`

Rebuild the **visual structure** while preserving what must not change: routes, information
architecture, and copy intent. You're re-dressing and re-shaping, not rewriting the product.

1. **Read the target and the room** (Step 0 of the Build Flow) — inherit real fonts/tokens where
   they're deliberate, and note what the current design gets *right* so you don't throw it away.
2. **Diagnose first.** Run the audit mentally so the redesign is aimed at real problems, not just
   change for its own sake.
3. **Preserve:** every route and link, the content and its meaning, any locked brand token
   (a fixed brand colour, a required logo). State explicitly what you're keeping.
4. **Change:** the Direction (pick one that serves the content better than the current shape), the
   Mood if the current one is generic or off-tone, the type scale, spacing rhythm, and states.
5. **Pick a Direction that differs from the current one** — a redesign that lands on the same
   skeleton rarely fixes anything. State: *"Was <old direction>; moving to <new> because <reason>."*
6. Build per the Build Flow (tokens, stamp, `tokens.css`) and run the Slop Check before handoff.

The line to hold: a redesign changes how it *looks and reads*, never what it *says* or where its
links *go*. If you find yourself rewriting the user's copy or dropping a route, stop — that's a
different request, and it should be the user's call.
