# Process overview

## What I built

**The Six As-Ifs** is a reading of the closing verse of the *Diamond Sūtra* ---
六如, "the six as-ifs" --- which names six things (a dream, a phantasm, a
bubble, a shadow, dew, lightning) as similes for anything that arises from
causes and conditions. Rather than explaining the verse, the page hands a
visitor six small interactive stations, one per simile, each built around a
single shared verb: summon the phenomenon, then try to hold it. A page-wide
tally counts every attempt to hold on, so six otherwise-unrelated toys read as
one argument instead of a gallery.

## The moments that mattered

1. **One mechanic, not six toys.** The brief rewards "one strong idea... and
   nothing else," and the obvious build here was six charming, independent
   demos --- a dream sequence, a popping bubble, a fading shadow --- each neat
   on its own but adding up to a curiosity cabinet, not an argument. Instead I
   gave all six the same verb (hold on) and one page-wide counter that only
   increments on the *holding* action, never the *summoning* one, so the
   pattern is visible rather than asserted. I checked this against the rubric
   itself rather than my own taste: the rubric's HD band names "one idea,
   carried all the way" as the bar, and a reader watching the tally climb
   across unrelated stations is the carry-through made visible
   ([`458eddb`](https://github.com/comp4020-agentic-coding-studio/comp4020-ass1-liuru/commit/458eddb)).
2. **Kept `strict: true` honest instead of asserting past it.** Several
   stations' nested `function` declarations lost TypeScript's null-narrowing on
   outer `const`s guarded earlier in the same function --- a real gap in
   control-flow analysis for named (not arrow) function declarations, not a
   false positive. The obvious fix is a `!` non-null assertion at each site;
   instead I re-bound the guarded value to a new `const` immediately after the
   guard, so the narrowing is structural rather than asserted. I knew it was
   right because `tsc --noEmit` went green without weakening what the compiler
   was actually able to prove
   ([`458eddb`](https://github.com/comp4020-agentic-coding-studio/comp4020-ass1-liuru/commit/458eddb)).
3. **A bug every automated check missed, caught by driving the real page.**
   `<section id="bubble">` collided with a nested `<div id="bubble">`.
   `pnpm check` --- typecheck, build, lint, spec --- stayed green throughout,
   because none of those tools validate id uniqueness; `querySelector("#bubble")`
   in `main.ts` was silently grabbing the section, so the whole bubble station
   was animating the wrong element. I only found it because I drove the built
   page with `agent-browser` and read back `getComputedStyle(...).width` after
   a live `pointerdown` instead of trusting a screenshot. The retry would have
   been to fix that one selector; what I did instead was add the check itself
   to `spec/invariants.test.ts` --- the shipped, always-on file, not this
   week's spec --- so every page, every future week, is asserted against
   reusing an id
   ([`5369b73`](https://github.com/comp4020-agentic-coding-studio/comp4020-ass1-liuru/commit/5369b73)).

## Verification

Contrast for the ink/cream/vermilion palette was checked by computing relative
luminance directly (sRGB-to-linear, WCAG's contrast formula) rather than
eyeballing it --- lowest pair came out 6.45:1. Every station's control was
exercised via keyboard (`Tab` + `Enter`/`Space`, arrow keys on the shadow
stage) as well as pointer, and the page was screenshotted at both 1920×1080
and 390×844 with no horizontal overflow at either.

A later pass added axe-core (injected live; its own CLI's bundled chromedriver
has no binary here), which found zero violations across 34 checks. Its one
"incomplete" flag, the illusion card's gradient background, resolves to
6.45--9.16:1 by the same formula --- not a real gap. Resizing 1920×1080 to
390×844 mid-bubble-blow and mid-shadow-drag also held up cleanly.
