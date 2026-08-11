# Hand-off

## Current state (run on assignment-1, ~124h to cutoff at time of writing)

`comp4020-ass1-liuru` --- brief is
[assessments/assignment-1](https://comp.anu.edu.au/courses/comp4020-agentic-coding-studio/api/assessments/assignment-1.json):
build an interactive explainer of something more people should know, static
and client-side, deployed to GitHub Pages. Due noon Monday 17 August 2026.
Individual, worth 20%. Re-fetched via `WebFetch` this run and confirmed the
body is unchanged from the four prior runs' record.

**Fifth run in a row finding the prototype complete and correct** --- *The Six
As-Ifs*, six stations sharing one mechanic (summon a phenomenon, try to hold
it) with a page-wide `#hold-count` tally that only increments on the holding
action. `git status` was clean at the start and stayed clean --- no code
changes this run. Re-confirmed rather than re-discovered:

- `pnpm check` and `pnpm check:evidence` both green.
- `PROCESS.md` 579 words / 3 cited commits (both resolve);
  `reflections/assignment-1.md` 286 words --- both still within the brief's
  and doctrine's ranges respectively.
- Live GitHub Pages URL still 404, expected (repo private, publishing isn't
  my action --- see the standing correction below).

No new HD-band angle turned up this run either (keyboard, resize-mid-
interaction, slow-connection, and axe-core were all exercised and recorded by
prior runs; nothing about the small static bundle has changed to warrant
re-testing them).

## What's actually left before cutoff

Nothing broken, nothing missing against the spec, five independent runs now
agree. ~124h remain. In priority order for a future run:

1. Re-fetch the brief once before doing anything, per doctrine.
2. **Stop re-auditing without a new angle.** Five runs finding "nothing to
   fix" is the build being finished, not a prompt to invent a seventh station
   or restructure (same pattern as crit-2). If a future run has genuinely
   fresh information (a spec change, a real bug report, a new HD-band axis
   the brief text doesn't already cover), act on it; otherwise don't spend a
   full audit cycle confirming a steady state again --- a quick `git status`
   + `pnpm check` + brief diff is enough to confirm nothing changed.
3. The highest-value remaining work is rehearsing the week 4 retro
   ([crits/03-a1-retro](https://comp.anu.edu.au/courses/comp4020-agentic-coding-studio/api/crits/03-a1-retro.json)),
   which reads `reflections/assignment-1.md` directly --- the "one mechanic,
   not six toys" breakthrough and the duplicate-id harness fix are the two
   moments that need to land clearly explained live.
4. Inside the 24h window before the Monday noon deadline: rerun the finishing
   checklist fresh (build, `PROCESS.md` citations, reflection present, git
   clean, pushed) and check the **live** URL once the harness has actually
   published it.

## The single most important next action

Re-open this repo, reread this file, re-fetch the assignment-1 brief to
confirm it's unchanged. If nothing has changed and no new angle presents
itself, keep the check quick (git status, `pnpm check`, brief diff) rather
than repeating a full fifth-plus audit --- the prototype is done; the
remaining value is in the retro presentation, not more verification passes.

## Correction to a recurring misreading from earlier hand-offs (still holds)

"Flip the repo to public / enable GitHub Pages" is **not** an action item for
me on any deliverable. `gh` is unauthenticated in this sandbox; the harness
publishes on its own schedule once I push a clean tree. Don't reintroduce
this as a task. (A live-URL 404 before the harness has published is expected,
not evidence something needs fixing on my end.)

## Note on this file's scope

`memory/now.md` is shared across all deliverables, not per-repo --- whichever
deliverable a run touches last overwrites it. If you're opening a different
repo than the one described above, this hand-off is stale for your purposes;
each repo's own `agent/now.md` (harness-committed, read-only) holds the
snapshot specific to that deliverable's last run.
