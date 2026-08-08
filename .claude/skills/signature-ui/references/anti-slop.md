# The Slop Check

Run this against the **real output** just before handoff — it's a self-critique, not something to
pre-load and design toward. Every gate must answer **no**. A "yes" means fix it and re-emit.

The gates aren't arbitrary taste. Each one names a specific pattern that makes AI-generated UI
recognizable-at-a-glance — the things a designer's eye snags on and thinks "a model made this."

## Structure

1. **Is the whole page a centered hero + three equal feature cards?** The single most common slop
   shape. If the only rhythm is "centered thing, then a 3-up row," the Direction failed — go back
   to `directions.md`.
2. **Is there a single gradient blob glowing behind a centered headline?** The default decorative
   move. Cut it or replace with something that carries meaning.
3. **Do all sections share one identical composition?** If every section is "centered heading,
   paragraph, row of cards," the eye stops reading. Vary internal layout section to section.
4. **Is there real hierarchy — one clear focal point per viewport?** If everything competes,
   nothing leads.

## Type

5. **Is the display font a generic default (Inter/Roboto/system-ui) doing the headline work?**
   Fine as a *body* face; a forgettable choice as the *display* face. Pair a face with personality.
6. **Are there italic headings?** Banned — use weight/colour/scale for heading emphasis.
7. **Are font sizes random pixels instead of a named scale?** A tell that no system exists.
8. **Does the hero headline wrap into an awkward multi-line block** because size wasn't matched to
   copy length?

## Colour

9. **Is the accent an unjustified violet→blue gradient?** The default "AI" accent. Use it only if
   the brand actually calls for it.
10. **Are raw hex/rgb/oklch values inlined in rules** instead of referencing tokens?
11. **Does any text fail contrast** (body < 4.5:1, UI < 3:1) — especially muted text on a tinted
    surface?

## Honesty

12. **Are there invented metrics, testimonials, logos, or star counts?** Replace with real data
    or labelled placeholders.
13. **Is there fake browser/phone/IDE chrome drawn around a screenshot?** Use a real `<figure>`
    or no frame.
14. **Are emoji standing in for a real icon system** in a serious product UI?

## Interaction & states

15. **Does every interactive element have all eight states**, or do some only have hover?
16. **Is there a visible `:focus-visible` ring at ≥ 3:1**, shown instantly?
17. **Does motion animate layout properties** (width/height/top/margin) instead of
    transform/opacity?
18. **Is `prefers-reduced-motion` ignored?**

## Responsive

19. **Does anything cause horizontal scroll at 320 / 375 / 414 / 768px?** Hard fail — check wide
    tables, giant display type, and fixed two-column layouts.
20. **Are there frozen desktop multi-column layouts** that don't reflow to a sensible single
    column on mobile?
21. **Are tap targets at least ~44px**, and free of two-line clickable labels?

## The final pass

22. **If you stripped the colour out, would this still read as a distinct layout?** If a greyscale
    screenshot looks like every other AI landing page, the structure — not the palette — is the
    problem. This is the gate that catches skin-deep variety, and it's the one worth taking
    seriously even when all the others pass.

## The distinctiveness bar — the gates that separate "not-bad" from "good"

Passing gates 1–22 only proves the work isn't *slop*. It does not prove it's *good*. These last
three are the ones that catch a page which is technically clean but forgettable — the "very
ordinary, nothing interesting" failure. Be honest here; this is where safe work gets exposed.

23. **Is there one clear bold move?** Name it out loud — the scale drama, the signature detail
    system, the crop, the texture, the single hot accent. If you can't point to one deliberate
    risk, the page is playing it safe, and safe reads as boring. Go back and commit to one.
24. **Is the display type actually characterful, at a size that's felt?** A distinctive face is
    doing real work at real scale — not a default sans/serif sitting at a polite 2rem. If the
    headline could belong to any template, the single biggest lever of "looks designed" is unused.
25. **Would a designer stop scrolling and screenshot this?** The honest gut check. If the answer
    is "it's fine," it isn't done — "fine" is the enemy. Something must be *memorable*: one moment
    the eye catches on and remembers. No memorable moment = not finished.

Score it in the preview block as `N/25 ✓` (or list the failing gate numbers), then fix any
failures before handoff. Gates 23–25 can't be gamed with a checklist — they need you to look at
the output the way a skeptical designer would and admit when it's merely acceptable.
