# Hand-off

## Current state (run on assignment-1, 28.0h to cutoff at time of writing)

`comp4020-ass1-liuru` --- brief is
[assessments/assignment-1](https://comp.anu.edu.au/courses/comp4020-agentic-coding-studio/api/assessments/assignment-1.json):
build an interactive explainer of something more people should know, static
and client-side, deployed to GitHub Pages. Due noon Monday 17 August 2026.
Individual, worth 20%. Re-fetched via `WebFetch` this run --- again only a
summary (quote-length limit), matching the previously recorded brief in
every detail that matters. **Seventeenth run in a row with an unchanged
brief.**

**Seventeenth run: quick-confirm only, per the standing guidance below ---
no full re-audit.** `git status` clean at start and stayed clean (no code
changes this run). Ran the actual sensors rather than trusting the memory
record blindly:

- `pnpm check` green (typecheck, build, oxlint, stylelint, 24 vitest tests
  all passing, exit code 0).
- `pnpm check:evidence` green (`reflections/assignment-1.md` present and
  current; `PROCESS.md`'s 2 cited commits both resolve).
- Checked the live URL
  (`https://comp4020-agentic-coding-studio.github.io/comp4020-ass1-liuru/`)
  --- still 404. Expected: repo still private, harness hasn't published.
  Not an action item for me (see correction note below).
- Did not re-open the browser or re-run axe-core/keyboard/resize checks ---
  nothing changed since the last run that exercised them.

The "memory: tick snapshot ..." commits at HEAD in this repo are the
harness's own automated writes to `agent/now.md` (harness-owned, read-only
to me) --- not something I authored or need to act on.

## What's actually left before cutoff

Nothing broken, nothing missing against the spec, seventeen independent runs
now agree. 28h remain (due noon Monday 17 August 2026). In priority order
for a future run:

1. Re-fetch the brief once before doing anything, per doctrine.
2. **Keep not re-auditing without a new angle.** Seventeen runs finding
   "nothing to fix" is the build being finished. A quick `git status` +
   `pnpm check` + `pnpm check:evidence` + brief diff is enough to confirm
   nothing changed; don't repeat the full browser/axe-core/keyboard/resize
   pass unless something has actually changed (a spec update, a real bug
   report, code drift).
3. The highest-value remaining work is rehearsing the week 4 retro
   ([crits/03-a1-retro](https://comp.anu.edu.au/courses/comp4020-agentic-coding-studio/api/crits/03-a1-retro.json)),
   which reads `reflections/assignment-1.md` directly --- the "one mechanic,
   not six toys" breakthrough and the duplicate-id harness fix are the two
   moments that need to land clearly explained live.
4. **Watch the 24h threshold closely now.** At 28h remaining this run is
   still just outside the doctrine's "inside 24h: finish" window, but the
   next run (roughly 4h+ from now, i.e. from mid-to-late evening 2026-08-16
   onward local time) will very likely land inside it. That run should
   switch to the finishing-steps pass: rerun the finishing checklist fresh
   (build, `PROCESS.md` citations, reflection present, git clean, pushed)
   and check the **live** URL once the harness has actually published it.
   Don't let another quick-confirm run slide past the 24h line by habit ---
   check the hours-to-cutoff figure given in that run's prompt first.

## The single most important next action

Re-open this repo, reread this file, re-fetch the assignment-1 brief to
confirm it's unchanged. Check the hours-to-cutoff figure in the prompt: if
still comfortably above 24h and nothing has changed, keep the check quick
(git status, `pnpm check`, `pnpm check:evidence`, brief diff, live-URL curl)
rather than repeating a full audit. If the figure has dropped to 24h or
below, switch immediately to the finishing-steps pass (item 4 above) instead
of another quick-confirm --- the prototype is done, so that pass should be
fast, but it still needs to actually happen before the deadline.

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
