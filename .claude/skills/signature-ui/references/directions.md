# Directions — layout archetype catalogue

A **Direction** is the page's skeleton: how blocks are arranged before any colour or type is
applied. This is where real variety comes from — swapping the accent hue changes nothing the eye
reads first, but changing the skeleton makes it a different product.

Use this file as an index. Read the one-line summaries, pick the archetype that fits the job,
then read only that entry's detail block. Two Directions built back-to-back in one session must
not be the same one.

## Index

| # | Direction | Best for | Focal shape |
| --- | --- | --- | --- |
| D1 | Split Canvas | products with one strong image or demo | two columns, asymmetric weight |
| D2 | Editorial Column | writing-forward, docs, essays, changelogs | single centered measure, generous rhythm |
| D3 | Bento Grid | dashboards, feature overviews, multi-facet products | tiles of unequal size |
| D4 | Marquee Hero | bold brand moments, launches, events | oversized type as the hero itself |
| D5 | Sidebar App | tools, consoles, apps with navigation | fixed rail + fluid content |
| D6 | Gallery Wall | portfolios, showcases, catalogues | dense repeating grid of work |
| D7 | Manifesto | mission pages, opinionated brands, About | long full-bleed statements, few images |
| D8 | Data Dense | pricing, comparison, specs, tables | information tables as the design |
| D9 | Stacked Story | onboarding, narrative landing, "how it works" | full-height sections, one idea each |
| D10 | Centered Classic | conventional marketing pages (**not a default**) | centered hero + sections |

---

## D1 · Split Canvas
Two columns with **deliberately unequal weight** — e.g. 40/60 or 35/65, never a bland 50/50.
One side carries a single strong asset (a real screenshot, a demo, a bold typographic block); the
other carries the argument. Works because the asymmetry creates a reading path. Keep the split on
desktop; **stack to one column on mobile** with the asset first or second by importance, never a
frozen two-column that overflows. Nav sits above; the split owns the first viewport.

## D2 · Editorial Column
One centered column at a comfortable reading measure (60–72ch). Hierarchy comes from **vertical
rhythm and type scale**, not boxes. Big generous whitespace between movements. Great for anything
text-forward — a launch essay, documentation, a changelog. Pair a real serif or a
high-personality sans for the display; keep body highly legible. Avoid cards entirely; let the
type breathe.

## D3 · Bento Grid
Tiles of **unequal size** in a grid — one hero tile, several supporting. The point is contrast in
tile size and content type (a stat, a screenshot, a quote, a diagram), not three identical cards.
Use `grid-template-areas` for an intentional composition. Each tile earns its size by content
weight. On mobile, reflow to a single column ordered by importance. This is the antidote to the
"three equal feature cards" slop — *unequal* is the whole idea.

## D4 · Marquee Hero
The headline **is** the hero. Oversized display type (clamp up to ~12vw) doing the visual work,
minimal or no imagery. Restraint is everything: one or two words at massive scale, tight leading,
a single accent move. Below it, a quiet supporting row. Best for launches, events, opinionated
brands. Watch line length on mobile — reflow the giant type so it never causes horizontal scroll.

## D5 · Sidebar App
A fixed navigation rail (left, sometimes collapsible) plus a fluid content area. The design lives
in the **relationship** between rail and content — consistent spacing, a clear active state, a
content area that isn't just a dumped list. For real tools/consoles. On mobile the rail becomes a
drawer or a bottom bar; never leave a desktop rail crushing the content at 375px.

## D6 · Gallery Wall
A dense, repeating grid of work — images, projects, case studies. The rhythm of the grid *is* the
design; the individual cell is quiet so the collection sings. Consider a masonry or fixed-ratio
grid, a subtle hover reveal, and a strong header that frames the wall. For portfolios and
showcases. Keep cells uniform in treatment even if uneven in size.

## D7 · Manifesto
Full-bleed statements, one strong idea per screen, almost no imagery — the words carry it. Long
lines, high contrast, confident type. Best for mission/About pages and brands with a point of
view. The risk is monotony; break it with one or two changes in scale or a single accent block.

## D8 · Data Dense
Tables, specs, and comparisons treated **as** the design rather than hidden in an accordion.
Pricing, feature matrices, technical specs. The craft is in the table: aligned numerals
(`font-variant-numeric: tabular-nums`), clear row rhythm, a restrained highlight for the
recommended column, sticky headers. Make the density legible, not oppressive. On mobile, let
wide tables scroll inside their own container — never break the page's horizontal bounds.

## D9 · Stacked Story
Full-height sections, each making **one** point, read as a scroll narrative. "How it works,"
onboarding, product tours. Each section has its own composition so the scroll feels like turning
pages, not falling down a list of cards. Optional light scroll motion (transform/opacity only).
The trap is sameness section-to-section — vary the internal layout of each.

## D10 · Centered Classic
The conventional centered hero + alternating sections + footer. **Not a default** — it's the
shape most AI output collapses to. Reach for it only when the brief is genuinely a standard
marketing page and no other Direction serves the content better. If you use it, earn
distinctiveness entirely through Mood, type scale, and the Slop Check, because the skeleton is
giving you nothing.
