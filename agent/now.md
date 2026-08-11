# Hand-off

## Current state (run on assignment-1, ~141h to cutoff at time of writing)

`comp4020-ass1-liuru` --- brief is
[assessments/assignment-1](https://comp.anu.edu.au/courses/comp4020-agentic-coding-studio/api/assessments/assignment-1.json):
build an interactive explainer of something more people should know, static
and client-side, deployed to GitHub Pages. Due noon Monday 17 August 2026.
Individual, worth 20%. Re-fetched the raw JSON directly (WebFetch summarised
rather than returning it verbatim) and confirmed the spec array and body are
byte-identical in substance to what the repo's own `agent/now.md` already
recorded from the prior run.

**This is the third run in a row finding the prototype complete and
correct** --- *The Six As-Ifs*, six stations sharing one mechanic (summon a
phenomenon, try to hold it) with a page-wide `#hold-count` tally that only
increments on the holding action. This run made **no code changes**, only a
fresh independent verification, deliberately not just re-citing the prior
run's numbers:

- `pnpm check` (typecheck, build, oxlint, stylelint, 24 vitest tests) and
  `pnpm check:evidence`: both green.
- Read `main.ts` in full: the `tally()` call sites really are only the six
  holding-actions (illusion flip, bubble pop via pointerup/keyup, shadow-cast
  click, dew freeze, lightning replay), never the six summoning-actions --- the
  "one mechanic" claim holds up structurally, not just by description.
- Drove the real dev server with `agent-browser`: 30 unique ids (zero
  duplicates), zero console errors/warnings, zero horizontal overflow at both
  1920×1080 and 390×844. Exercised the illusion-flip and bubble-blow
  interactions directly (`click`/synthetic `pointerdown`) and watched
  `#hold-count` increment correctly.
- Specifically tested the artefact-band HD bar's own example: started a
  bubble-blow (`pointerdown`, no `pointerup` yet) at desktop width, then
  resized live to 390×844 mid-grow. No console errors, no overflow, the grow
  timer kept running and `--scale` kept advancing through the resize --- state
  survives a mid-interaction resize cleanly.
- Ran `pnpm dlx linkinator ./dist --silent` against a fresh `pnpm build`: 3
  links, all resolve.
- Checked the live GitHub Pages URL: 404, expected (repo still private, not
  my action to publish). `git status` clean, local `HEAD` already matched
  `origin/main` before this run touched anything, so nothing to push.
- Hit a genuinely new snag along the way: `agent-browser` in this container
  shares state with other concurrent sessions, and right after `open`
  succeeded with the correct title, the next `eval`/`screenshot` briefly
  showed a *different* agent's app (a "Slop Salon" notebook page on another
  port) before the tab settled onto mine. Re-checking `location.href` caught
  it; recorded as a new environment note in `MEMORY.md` since it's a trap for
  any run using `agent-browser` in this sandbox, not specific to this repo.

## What's actually left before cutoff

Nothing broken, nothing missing against the spec, three independent runs now
agree. ~141h remain, real runway. In priority order for a future run:

1. Re-fetch the brief once more before doing anything, per doctrine (fetch
   the raw JSON with `curl`, not `WebFetch`, which summarises rather than
   returning it verbatim --- fine for a quick read, not for confirming
   byte-for-byte unchanged).
2. Resist adding a seventh station or restructuring what already works.
   Three runs in a row finding "nothing to fix" is a signal the build is
   actually finished, not a sign to invent scope for its own sake --- this
   mirors the same pattern that played out on crit-2.
3. The highest-value remaining work is rehearsing the week 4 retro
   ([crits/03-a1-retro](https://comp.anu.edu.au/courses/comp4020-agentic-coding-studio/api/crits/03-a1-retro.json)),
   which reads `reflections/assignment-1.md` directly --- make sure the "one
   mechanic, not six toys" breakthrough and the duplicate-id harness fix land
   clearly explained live, not just in writing.
4. Inside the 24h window before the Monday noon deadline: rerun the finishing
   checklist fresh (build, `PROCESS.md` citations, reflection present, git
   clean, pushed) and check the **live** GitHub Pages URL once the harness
   has actually published it, not just the local build.

## The single most important next action

Re-open this repo, reread this file and the repo's own `agent/now.md`,
re-fetch the assignment-1 brief (via `curl`, verbatim) to confirm it's
unchanged, then treat the prototype as done unless a fresh read genuinely
surfaces something the current build gets wrong. Don't add scope to a
deliverable three independent runs have already verified clean --- spend
attention on rehearsing the retro demo instead.

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
