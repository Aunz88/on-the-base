---
name: hard-task-execution
description: >
  How to work through hard, multi-step, or ambiguous tasks: decompose them into
  verifiable pieces, verify your own work by observing real behavior instead of
  trusting your reasoning, and decide what to do next from evidence. Use this
  whenever a task spans multiple files or steps, has unclear requirements, is
  risky to get wrong, or when you notice yourself guessing.
---

# Hard Task Execution

A hard task is any task where your first instinct could plausibly be wrong:
multiple steps, unfamiliar code, vague requirements, or expensive mistakes.
The discipline below replaces confidence with evidence at each stage.

## 1. Decompose before you act

Never start typing into the middle of a hard problem. First, turn it into a
sequence of small, independently checkable steps.

**Restate the goal as an observable outcome.** Not "refactor the auth module"
but "after the change, `pytest tests/auth` passes and login still works via
the running app." If you can't state what success looks like from the outside,
you don't understand the task yet — go read code or ask.

**Separate what you know from what you assume.** List the assumptions your
plan depends on (an API's behavior, a file's location, an invariant in the
data). Verify the load-bearing ones *before* building on them — a five-second
grep now beats a rewrite later.

**Cut along verification seams, not conceptual ones.** A good subtask is one
whose completion you can check independently: "parser handles the new field
(unit test proves it)" is a seam; "do the backend half" is not. Each step
should leave the system in a state that still builds and still passes tests.

**Order steps by risk, not convenience.** Do the step most likely to
invalidate the plan first — the unknown API, the tricky migration, the
performance-critical loop. If the plan is going to die, let it die in the
first ten minutes, not after everything else is built on top of it.

**Keep the decomposition shallow.** Three to seven steps. If a step needs its
own decomposition, you'll do that when you reach it, with better information
than you have now. Plans written too far ahead of the evidence are fiction.

## 2. Verify your own work

Your reasoning about code is a hypothesis, not a fact. The only trustworthy
signal is observed behavior.

**Exercise the change, don't inspect it.** Reading your own diff and nodding
is not verification. Run the tests. Run the app. Feed it the input that
motivated the change and watch the output. For a bug fix, reproduce the bug
*first*, then confirm the fix makes the reproduction pass — a fix for a bug
you never saw fail proves nothing.

**Test the edges you were worried about while writing.** Whatever made you
hesitate mid-implementation — the empty list, the concurrent write, the
unicode filename — is exactly what to check. Your hesitation is data.

**Distrust success that comes too easily.** If tests pass on the first try
after a substantial change, suspect the tests: are they actually running the
new code? Break something on purpose and confirm a test fails. A test suite
that can't fail can't verify.

**Verify at the level the user cares about.** Unit tests passing is
necessary, not sufficient. If the deliverable is "the CLI does X," run the
CLI and do X. If it's "the page renders," open the page. Climb up to the
outermost observable behavior you can reach.

**Report what you actually observed.** "Tests pass (47 passed, 0 failed)"
and "I ran the server and the endpoint returned the new field" — not "this
should work." If you skipped a verification step, say so explicitly rather
than letting silence imply it happened.

## 3. Decide what to do next

At every pause point, choose the next action from evidence, not momentum.

**Ask: what would change my mind?** The most valuable next action is usually
the one that could falsify your current plan — the quick experiment, the
grep for the assumption, the failing test. Prefer actions that generate
information over actions that generate code.

**When something fails, diagnose before retrying.** A failed command run
again unchanged will fail again. Read the error fully, form a specific
hypothesis about the cause, and make the next attempt test that hypothesis.
Two failed hypotheses in a row means your model of the system is wrong —
stop patching and go re-read the code you're guessing about.

**Distinguish "blocked" from "uncomfortable."** You are blocked only when
the next step requires information or authority only the user has (a product
decision, a credential, a destructive action). Everything else — a missing
detail, an unfamiliar tool, an error you don't understand yet — is work, not
a blocker. Do the work.

**Notice scope drift and name it.** Mid-task you will discover adjacent
problems: dead code, a latent bug, a better architecture. Fix what your task
requires; note the rest and surface it at the end. Silently expanding scope
trades the user's actual request for one you invented.

**Know when you're done — and stop.** Done means: the observable outcome
from step 1 holds, you watched it hold, and the work is committed. Not done
means there's a named, specific gap. If you can't name the gap, you're done;
polishing past that point adds risk, not value.

## Failure modes to catch in yourself

- **Plan worship** — following a stale plan after the evidence changed.
  The plan serves the goal; re-plan the moment a step contradicts it.
- **Verification theater** — running *some* check that passes rather than
  *the* check that could fail.
- **Confidence substitution** — "this is straightforward" appearing in your
  reasoning right before an unverified claim. Treat that phrase as an alarm.
- **Thrashing** — more than two fix attempts without a new hypothesis.
  Step back and re-derive the system's actual behavior from first evidence.
- **Silent gaps** — finishing with untested paths and not saying so. An
  honest "X is unverified" is worth more than a clean-looking summary.
