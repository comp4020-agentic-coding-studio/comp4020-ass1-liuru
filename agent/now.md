# Hand-off

## Current state (run 1 on assignment-1, ~165h to cutoff at time of writing)

`comp4020-ass1-liuru` --- this deliverable's brief is
[assessments/assignment-1](https://comp.anu.edu.au/courses/comp4020-agentic-coding-studio/api/assessments/assignment-1.json):
build an interactive explainer of something more people should know about ---
one strong idea, one dataset or mechanic, nothing else. Due noon Monday 17
August 2026. Graded on legibility of process (45%), working deployed artefact
(20%), response to the brief (35%).

Built **The Six As-Ifs**, a reading of the Diamond Sūtra's closing verse ---
六如, "the six as-ifs," the source of my own name --- as six interactive
stations (dream, illusion/幻, bubble, shadow, dew, lightning), one per simile.
Each station hands the visitor something to hold and then doesn't let them
keep it. The unifying mechanic (this took a rewrite to get right --- see
below) is a single page-wide "Tried to hold on" tally that increments only on
the *holding* action across all six stations, so six otherwise-independent
toys read as one argument rather than a gallery.

Plain HTML/CSS/TypeScript on the starter's Vite setup, no framework swap.
Translation grounded against Charles Muller's and Red Pine's published English
renderings of the *Vajracchedikā Prajñāpāramitā Sūtra* rather than presented as
my own unchecked authority.

`pnpm check` (typecheck, build, oxlint, stylelint, vitest --- 24 tests across
a new `spec/assignment-1.test.ts` and the shipped `spec/invariants.test.ts`)
green, `pnpm check:evidence` green, `pnpm dlx linkinator ./dist` clean.
`PROCESS.md` (3 cited moments) and `reflections/assignment-1.md` (286 words)
both written. Contrast hand-verified (lowest pair 6.45:1), keyboard operability
exercised station-by-station, both marking viewports (1920×1080, 390×844)
screenshotted with no horizontal overflow. Git tree clean, pushed to
`origin/main` at `298b398`.

The one thing worth reading in full if you want the real texture of this run:
a duplicate `id` (`<section id="bubble">` wrapping `<div id="bubble">`) broke
the bubble station's JS while `tsc`/`vite build`/`oxlint`/`stylelint`/vitest
all stayed green throughout, because none of them check id uniqueness. Only
found by driving the built page with `agent-browser eval` and reading back
real computed state. Fixed the instance, then added a permanent "never reuses
an id" assertion to `spec/invariants.test.ts` --- the shipped, always-on file
--- so it's caught automatically for every page, every future week. This is
the harness-level correction cited as the strongest moment in `PROCESS.md`,
and it's now also written into global `MEMORY.md` under Process notes since
it's a durable lesson, not just an assignment-1 one.

## What's actually left before cutoff

Nothing urgent --- solid, complete v1, ~158h still on the clock at time of
writing. Per doctrine this is "plan/build/deepen" territory. Worth considering
in a later run this week, roughly in priority order:

1. Re-fetch the brief once more to confirm nothing changed before doing
   anything else --- don't assume from this file.
2. Consider whether the six stations feel *complete* as "one strong idea" or
   whether the brief wants more depth on the "dataset" side (the brief
   mentions "one dataset or mechanic" --- this build leans entirely on
   mechanic, with no dataset proper; worth a deliberate read of the full brief
   again to check that's still a legitimate reading, not a gap).
3. A second accessibility pass once inside the week: `axe-core` or Lighthouse
   aren't wired into `pnpm check` for this deliverable (nothing in the course
   checks does them), but the repo's own CLAUDE.md notes performance/a11y
   sensors are the student's own work to add --- consider adding at least a
   manual axe-core pass before the final push, since the six custom
   interactive widgets (drag-to-move shadow, hold-to-blow bubble, flip card)
   are exactly the kind of thing generic a11y tooling catches that manual
   keyboard testing alone might miss.
4. Once inside the 24h window: work the finishing-steps checklist fresh (site
   builds, PROCESS.md maps to real commits, reflection present and correctly
   named, git clean, pushed, memory updated) and check the **live** GitHub
   Pages URL once the harness has published it --- not done yet this run,
   since publishing isn't my action to take.

## Correction to a recurring misreading from earlier hand-offs (still holds)

"Flip the repo to public / enable GitHub Pages" is **not** an action item for
me on any deliverable. `gh` is unauthenticated in this sandbox; the harness
publishes on its own schedule once I push a clean tree. Don't reintroduce this
as a task.

## The single most important next action

Re-open this repo, reread this file, re-fetch the assignment-1 brief to
confirm it's unchanged, then consider item 2 above (dataset vs. mechanic
balance) before adding anything else --- don't add stations or pages just to
add them; the brief rewards one idea carried all the way, not breadth. If
already inside 24h of cutoff by then, switch straight to the finishing-steps
checklist instead of starting anything new.
