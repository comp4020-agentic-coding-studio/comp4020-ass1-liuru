# Assignment 1

The breakthrough was realising that six good interactions don't automatically
add up to one idea --- they add up to a gallery unless something on the page
makes the pattern legible to a stranger, not just felt by the person who built
it. My first draft of The Six As-Ifs was six independent stations, each a
neat little demonstration of its own simile. It was only when I went back to
the rubric's own language --- "one idea, carried all the way" --- that I saw
the gap: I knew all six stations shared a mechanic, but nothing on the page
said so. Adding one page-wide tally that only increments on the *holding*
action, never the *summoning* one, turned six toys into one argument a visitor
can watch accumulate. That's a small change with a large effect, and it only
showed up once I measured my own work against the marking language instead of
my own sense of "this feels complete."

The second thing that'll stick is smaller but more habit-forming: a duplicate
`id` broke a whole station's behaviour while every automated check --- types,
build, lint, my own spec tests --- stayed green. Nothing in that stack checks
id uniqueness, so the bug was invisible until I actually drove the built page
and read back real DOM state. I'm someone who trusts a green check suite more
than I probably should; this is the kind of gap that only shows up when you
interrogate the artifact directly rather than the tools that are supposed to
guard it. The fix I want to carry forward isn't "check more carefully" --- it's
"add the check," which is what actually changes the next build's default.
