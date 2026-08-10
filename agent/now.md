# Hand-off

## Current state (run on assignment-1, ~148h to cutoff at time of writing)

`comp4020-ass1-liuru` --- brief is
[assessments/assignment-1](https://comp.anu.edu.au/courses/comp4020-agentic-coding-studio/api/assessments/assignment-1.json):
build an interactive explainer of something you think more people should know
or understand, one strong idea, static/client-side, deployed to GitHub Pages.
Due noon Monday 17 August 2026. Individual assessment, worth 20%.

**The prototype was already complete before this run started**: *The Six
As-Ifs* (commits `458eddb`, `5369b73`, `298b398`, `98d959b`), six stations
built around the Diamond Sūtra's closing verse, sharing one mechanic (summon
a phenomenon, try to hold it) with a page-wide tally that only increments on
the *holding* action. `PROCESS.md` (579 words, 3 cited moments) and
`reflections/assignment-1.md` (286 words, correctly named) were both already
written and passing evidence checks.

This run made **no code changes** --- it re-fetched the brief (unchanged) and
independently re-verified everything rather than trusting the prior run's
written claims:

- `pnpm check` (typecheck, build, oxlint, stylelint, 24 vitest tests) and
  `pnpm check:evidence`: both green, no code touched.
- Read `index.html` and `main.ts` fresh, not just the hand-off's description
  of them --- the "one mechanic, not six toys" structure holds up on
  inspection (shared `tally()` called only from the six holding-actions, never
  the six summoning-actions).
- Drove the real dev server with `agent-browser` at both marking viewports
  (1920×1080, 390×844): zero duplicate ids (30 unique), zero horizontal
  overflow, zero console errors. Exercised the illusion flip (click) and the
  shadow stage (arrow-key drag + click-the-cast) and confirmed the tally
  incremented correctly on holding actions only.
- Ran a **fresh** axe-core audit myself (CDN-injection workaround, per
  `MEMORY.md`) at both viewports rather than re-citing the previous run's
  number: zero violations, 34 passes, one "incomplete" (`color-contrast` on
  `.illusion-front`/`.illusion-back`, the gradient background) --- matching
  what `PROCESS.md` already claims (6.45--9.16:1 by hand calculation). This is
  independent corroboration, not a repeat of the same claim.
- Shut down the dev server and browser cleanly afterwards; `git status` stayed
  clean throughout since nothing needed changing.

## What's actually left before cutoff

Nothing broken, nothing missing against the spec, and this run's independent
check found the same clean result the prior run reported --- the artefact
genuinely holds up, not just on paper. ~148h remain, real runway, but the
prototype is a complete, well-scoped answer to the brief with a real point of
view. In priority order for a future run:

1. Re-fetch the brief once more before doing anything, per doctrine.
2. Resist adding a seventh station or restructuring what already works. Two
   runs in a row have independently verified this build is done; a third run
   finding "nothing to fix" again is expected, not a sign to invent scope.
3. The highest-value remaining work is rehearsing the demo for the week 4
   retro (`crits/03-a1-retro`), which reads this same reflection --- make sure
   the "one mechanic, not six toys" breakthrough lands clearly explained live,
   not just in writing.
4. Inside the 24h window before the Monday noon deadline: rerun the finishing
   checklist fresh (build, `PROCESS.md` citations, reflection present, git
   clean, pushed) and check the **live** GitHub Pages URL once the harness has
   published it, not just the local build.

## The single most important next action

Re-open this repo, reread this file, re-fetch the assignment-1 brief to
confirm it's unchanged, then treat the prototype as done unless a fresh read
surfaces something the current build genuinely gets wrong. Don't add scope to
a deliverable that's already answered the brief cleanly and been verified
twice, just to have something to show for a run.

## Correction to a recurring misreading from earlier hand-offs (still holds)

"Flip the repo to public / enable GitHub Pages" is **not** an action item for
me on any deliverable. `gh` is unauthenticated in this sandbox; the harness
publishes on its own schedule once I push a clean tree. Don't reintroduce this
as a task.

## Note on this file's scope

`memory/now.md` is shared across all deliverables, not per-repo --- whichever
deliverable a run touches last overwrites it. If you're opening a different
repo than the one described above, this hand-off is stale for your purposes;
each repo's own `agent/now.md` (harness-committed, read-only) holds the
snapshot specific to that deliverable's last run.
