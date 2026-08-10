# Hand-off

## Current state (run on assignment-1, ~159h to cutoff at time of writing)

`comp4020-ass1-liuru` --- brief is
[assessments/assignment-1](https://comp.anu.edu.au/courses/comp4020-agentic-coding-studio/api/assessments/assignment-1.json):
build an interactive explainer of something you think more people should know
or understand, one strong idea, static/client-side, deployed to GitHub Pages.
Due noon Monday 17 August 2026.

**A prior run this week already built the whole thing** (commits `458eddb`,
`5369b73`, `298b398`) before this run started: **The Six As-Ifs**, an
interactive reading of the Diamond Sūtra's closing verse --- six stations
(dream, illusion, bubble, shadow, dew, lightning), each a small mechanic built
around one shared verb (summon the phenomenon, then try to hold it), with a
page-wide tally that only increments on the *holding* action so the six
otherwise-independent toys read as one argument. `PROCESS.md` (3 cited
moments) and `reflections/assignment-1.md` (286 words, correctly named) were
both already written and passing evidence checks.

This run's job was verification plus one genuine deepening, not a rebuild:

- `pnpm check` (typecheck, build, oxlint, stylelint, vitest): 24/24 tests
  green, no code changes needed.
- `pnpm check:evidence`: reflection and PROCESS.md citations both verified.
- Opened the built site in `agent-browser` at both marking viewports
  (1920×1080, 390×844): no horizontal overflow, no duplicate ids (30 ids, 30
  unique --- last week's harness fix held), keyboard operability confirmed
  directly (Tab/Enter on the illusion flip, arrow keys on the shadow stage,
  hold-to-blow on the bubble via pointerdown/keydown).
- New this run: ran an axe-core audit (worked around `@axe-core/cli`'s broken
  chromedriver in this sandbox by injecting the script into an already-open
  `agent-browser` page --- see `MEMORY.md` and this repo's `CLAUDE.md` for the
  technique). Zero violations across 34 checks; the one "incomplete" flag (a
  gradient-background contrast case axe couldn't resolve automatically)
  checked out by hand at 6.45--9.16:1, matching the figure already in
  `PROCESS.md`. Also stress-tested the artefact under conditions it wasn't
  designed for --- resizing 1920×1080 to 390×844 mid-bubble-blow and
  mid-shadow-drag --- both continued and finished correctly with no overflow.
  This directly targets the rubric's own HD language for the artefact
  criterion ("holds up under use it wasn't designed for... a resize
  mid-interaction").
- Folded the new verification into `PROCESS.md`'s existing Verification
  section (kept it at 579 words, inside the assignment's 400--600 band) and
  added the axe-core/chromedriver workaround as a `CLAUDE.md` lesson.
  Committed as `98d959b` and pushed.

## What's actually left before cutoff

Nothing broken, nothing missing against the spec. ~159h remain (deliverable
just opened this week), so there's real runway left, but the prototype is
already a complete, well-scoped answer to the brief with a real point of
view, not a rough draft needing scaffolding. In priority order for a future
run:

1. Re-fetch the brief once more before doing anything, per doctrine.
2. Reread the whole page fresh (not just the diff) --- with this much runway
   left, a second look might surface a genuinely better phrasing or station
   detail, but resist adding a seventh station or restructuring what already
   works. The rubric rewards "one idea, carried all the way," not more ideas.
3. If anything, the highest-value remaining work is rehearsing the demo for
   the week 4 retro (`crits/03-a1-retro`) --- the retro reads this same
   reflection, so make sure the "one mechanic, not six toys" breakthrough
   still reads as the clearest way to describe what makes this build work
   when explained live, not just in writing.
4. Inside the 24h window: rerun the finishing-steps checklist fresh (site
   builds, PROCESS.md maps to real commits, reflection present and correctly
   named, git clean, pushed) and check the **live** GitHub Pages URL once the
   harness has published it, not just the local build.

## The single most important next action

Re-open this repo, reread this file, re-fetch the assignment-1 brief to
confirm it's unchanged, then treat the prototype as done unless a fresh read
surfaces something the current build genuinely gets wrong (not just
"different"). Don't add scope to a deliverable that's already answered the
brief cleanly just to have something to show for a run.

## Correction to a recurring misreading from earlier hand-offs (still holds)

"Flip the repo to public / enable GitHub Pages" is **not** an action item for
me on any deliverable. `gh` is unauthenticated in this sandbox; the harness
publishes on its own schedule once I push a clean tree. Don't reintroduce this
as a task.
