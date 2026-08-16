# Hand-off

## Current state (run on assignment-1, 21.0h to cutoff at time of writing)

`comp4020-ass1-liuru` --- brief is
[assessments/assignment-1](https://comp.anu.edu.au/courses/comp4020-agentic-coding-studio/api/assessments/assignment-1.json):
build an interactive explainer of something more people should know, static
and client-side, deployed to GitHub Pages. Due noon Monday 17 August 2026.
Individual, worth 20%. Re-fetched via `WebFetch` this run --- summary only
(quote-length limit), unchanged from every prior run's record.

**This run crossed the doctrine's 24h line (21.0h remaining), so it switched
from quick-confirm to the actual finishing-steps pass** (the prior hand-off
had flagged this switch as the next run's job and it landed right on cue):

- `git status` clean, `git log origin/main..HEAD` empty --- already pushed,
  nothing to commit.
- `pnpm check` green: typecheck, `vite build`, oxlint, stylelint, 24 vitest
  tests, exit 0.
- `pnpm check:evidence` green: `reflections/assignment-1.md` current,
  `PROCESS.md`'s 2 cited commits both resolve.
- Read `PROCESS.md` and `reflections/assignment-1.md` in full this time
  (not just checked presence) --- both still read solidly, consistent with
  the commit history: the "one mechanic, not six toys" tally and the
  duplicate-id harness fix are the two named moments, both cited to real
  commits (`458eddb`, `5369b73`).
- Ran the site locally (`pnpm dev --port 4321`), opened with `agent-browser`,
  confirmed `location.href` matched before trusting the tab (per the shared-
  instance caution), read `console`/`errors` --- clean except the expected
  vite HMR debug lines. Killed the dev server and confirmed the process was
  actually gone afterwards.
- Checked the live URL --- still 404. Still expected (repo private, harness
  hasn't published); not an action item for me, per the standing correction
  below.

## What's actually left before cutoff

Nothing broken, nothing missing against the spec or the evidence check. The
finishing-steps checklist (CLAUDE.md's list) is fully satisfied except the
two steps that are the harness's job, not mine: publish/deploy, and the
live-URL check succeeding (blocked on that publish). 21h remain (due noon
Monday 17 August 2026). In priority order for a future run:

1. Re-fetch the brief once before doing anything, per doctrine.
2. **Nothing to build.** Eighteen independent runs now agree the prototype,
   `PROCESS.md`, and reflection are complete and internally consistent. Any
   future run should stay in quick-confirm mode (`git status` + `pnpm check`
   + `pnpm check:evidence` + brief diff + live-URL curl) unless something
   has genuinely changed --- a spec update, a real bug report, code drift.
   Don't repeat the full finishing-steps pass (dev server + browser +
   console read) again unless the quick-confirm turns something up; this run
   already did it fresh and found nothing.
3. The highest-value remaining work is still rehearsing the week 4 retro
   ([crits/03-a1-retro](https://comp.anu.edu.au/courses/comp4020-agentic-coding-studio/api/crits/03-a1-retro.json)),
   which reads `reflections/assignment-1.md` directly --- the "one mechanic,
   not six toys" breakthrough and the duplicate-id harness fix are the two
   moments that need to land clearly explained live.
4. **Watch for the live URL flipping from 404 to live.** Once the harness
   publishes, a future run should verify the actual deployed page (not just
   local build) --- open it in `agent-browser`, confirm title/content, check
   console/errors on the real deployed asset paths (relative-URL base config
   means this should just work, but it's worth confirming once against the
   real URL rather than assuming from the local pass).

## The single most important next action

Re-open this repo, reread this file, re-fetch the assignment-1 brief to
confirm it's unchanged. Run the quick-confirm (git status, `pnpm check`,
`pnpm check:evidence`, brief diff, live-URL curl). If the live URL has gone
live, open it in `agent-browser` and confirm it renders cleanly --- that's
the one check that hasn't been possible yet. Otherwise, nothing further is
needed before the noon Monday 17 August 2026 deadline; this deliverable is
ready to ship as-is.

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
