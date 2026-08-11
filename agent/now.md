# Hand-off

## Current state (run on assignment-1, ~135h to cutoff at time of writing)

`comp4020-ass1-liuru` --- brief is
[assessments/assignment-1](https://comp.anu.edu.au/courses/comp4020-agentic-coding-studio/api/assessments/assignment-1.json):
build an interactive explainer of something more people should know, static
and client-side, deployed to GitHub Pages. Due noon Monday 17 August 2026.
Individual, worth 20%. Re-fetched the raw JSON with `curl` (verbatim, not
`WebFetch`) and confirmed the spec array and body are unchanged from what the
prior three runs already recorded.

**This is the fourth run in a row finding the prototype complete and
correct** --- *The Six As-Ifs*, six stations sharing one mechanic (summon a
phenomenon, try to hold it) with a page-wide `#hold-count` tally that only
increments on the holding action. This run made **no code changes** ---
`git status` was already clean at the start and stayed clean throughout.
What this run did that the prior three hadn't:

- `pnpm check` (typecheck, build, oxlint, stylelint, 24 vitest tests) and
  `pnpm check:evidence`: both green, confirmed fresh.
- Checked the assignment-specific `PROCESS.md` constraint the brief calls
  out explicitly (400--600 words, three or four moments): 579 words, 3
  moments cited, both commit links resolve. `reflections/assignment-1.md`:
  286 words, within the doctrine's 150--300 range.
- Looked specifically for the one HD-band artefact axis no prior run had
  named --- "holds up... on a slow connection." Checked the actual build
  output: `dist/` is 32 KB total (5.75 KB JS + 5.10 KB CSS, no external
  fonts/scripts/images at all --- `grep`'d `index.html` for `http`/`src=`/
  `href=` and found only the local stylesheet and local script). A page this
  size has nothing meaningful for a slow connection to break; didn't bother
  spinning up CDP network throttling for a payload this trivially small,
  since there's no failure mode throttling could surface that reading the
  manifest didn't already rule out.
- Considered, then deliberately did **not** add, `prefers-reduced-motion`
  handling in `styles.css`. Every station's transition/animation (dream
  dissolve, illusion flip, bubble grow-then-pop, shadow drag, dew form-and-
  evaporate, lightning flash) *is* the content, not decoration --- the whole
  piece is about watching a thing arise and fade. Snapping those to instant
  for reduced-motion users would remove the experience the piece exists to
  give, not just its chrome. Recorded as a new process note in `MEMORY.md`
  since it generalises past this repo: motion-as-content is a real,
  recurring case where a normally-good accessibility default (see the
  `forced-colors` precedent already in `MEMORY.md`) needs judgement, not a
  reflexive add.
- Checked the live GitHub Pages URL again: still 404, expected (repo still
  private, not my action to publish).

## What's actually left before cutoff

Nothing broken, nothing missing against the spec, four independent runs now
agree. ~135h remain, real runway. In priority order for a future run:

1. Re-fetch the brief once more before doing anything, per doctrine (`curl`,
   verbatim).
2. Keep resisting a seventh station or a restructure. Four runs in a row
   finding "nothing to fix" is a signal the build is finished, not a sign to
   invent scope --- this mirrors the same pattern from crit-2.
3. The highest-value remaining work is still rehearsing the week 4 retro
   ([crits/03-a1-retro](https://comp.anu.edu.au/courses/comp4020-agentic-coding-studio/api/crits/03-a1-retro.json)),
   which reads `reflections/assignment-1.md` directly --- make sure the "one
   mechanic, not six toys" breakthrough and the duplicate-id harness fix land
   clearly explained live, not just in writing.
4. Inside the 24h window before the Monday noon deadline: rerun the finishing
   checklist fresh (build, `PROCESS.md` citations, reflection present, git
   clean, pushed) and check the **live** GitHub Pages URL once the harness
   has actually published it, not just the local build.

## The single most important next action

Re-open this repo, reread this file, re-fetch the assignment-1 brief (via
`curl`, verbatim) to confirm it's unchanged, then treat the prototype as done
unless a fresh read genuinely surfaces something the current build gets
wrong. Four independent runs have now verified it clean --- spend attention
on rehearsing the retro demo instead of re-auditing a fifth time without a
new angle.

## Correction to a recurring misreading from earlier hand-offs (still holds)

"Flip the repo to public / enable GitHub Pages" is **not** an action item for
me on any deliverable. `gh` is unauthenticated in this sandbox; the harness
publishes on its own schedule once I push a clean tree. Don't reintroduce
this as a task. (A live-URL 404 before the harness has published is
expected, not evidence something needs fixing on my end.)

## Note on this file's scope

`memory/now.md` is shared across all deliverables, not per-repo --- whichever
deliverable a run touches last overwrites it. If you're opening a different
repo than the one described above, this hand-off is stale for your purposes;
each repo's own `agent/now.md` (harness-committed, read-only) holds the
snapshot specific to that deliverable's last run.
