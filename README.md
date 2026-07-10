# TrailGear Co. — Performance Rescue Challenge (Expert Tier)

This is a working demo storefront. It runs, it looks fine at a glance — and it's slow
in ways that get worse the longer you use it, some of which won't show up in a quick
Lighthouse run at all. Your job is to find out why and fix it.

## The brief

TrailGear Co.'s site is live, but customers are complaining: pages take a while to
feel "ready," scrolling feels janky, the tab seems to get sluggish the longer it stays
open, and one engineer swears the fan on their laptop spins up "for no reason" after
using the site for a few minutes. Nobody on the team can say exactly why — that's
where you come in.

**Diagnose and fix as many real performance problems as you can find.** There are a
lot, at every level (network, CSS, DOM, JavaScript, memory). Some are visible within
seconds of opening DevTools. Others only show up after you interact with the page for
a while, open and close a few things, or look at a heap snapshot instead of a
timeline. A few look like reasonable, even performance-conscious code at first
read — the bug is in the logic, not in the obviousness of the anti-pattern.

This version is intentionally hard. Treat it like a real production incident:
some fixes are one-line, some require you to trace *why* something that looks
correct isn't behaving correctly.

## Running it locally

This is a static site with no build step, but it fetches a local JSON file, so it
needs to be served rather than opened directly as a `file://` URL. Any simple local
server works, for example:

```bash
# Python
python3 -m http.server 8080

# or Node
npx serve .
```

Then open `http://localhost:8080` in Chrome (DevTools performance and memory tooling
is most reliable there). For the issues that build up over time, leave the tab open
and interact with it (scroll, open/close Quick View a few times) for a few minutes
before judging whether something is fixed.

## What "done" looks like

You don't need to fix everything to submit something worthwhile — partial,
well-explained progress is fine, and this is deliberately more than most people will
finish. For whatever you do fix, we want to see:

1. **Before / after Lighthouse reports** (Performance tab) — screenshots or exported JSON.
2. **A short WRITEUP.md** listing each issue you found, how you diagnosed it (what
   tool, what you saw, and — for the trickier ones — what made you suspicious enough
   to go looking), and what you changed to fix it.
3. **Your fixed code**, committed with reasonably clear commit messages — we're
   interested in your process, not just a final diff.

## Ground rules

- Don't rewrite the site from scratch in a different framework — fix what's there.
- Don't just delete features to make them "not slow anymore" (e.g. removing the
  reviews section, the Quick View modal, or the analytics tracking entirely). Fix the
  underlying problem while keeping the feature working.
- Free tools only: Chrome DevTools and Lighthouse (built into Chrome) are all you need.
- If you run out of time, tell us what you'd do next in WRITEUP.md — that's worth
  real credit.

## Time guidance

Budget 2–3 hours. This is meant to be a genuine, fairly deep diagnostic exercise —
depth of understanding and the trickier catches matter more than raw fix count.

Good luck — and don't peek at the "given" column if we ever hand you a scoring sheet. 😉

# Issues Found 

duplicate Jquery librry was found
legancy polyfill was loaded unnescessary fo all browser
rendr blocking js affected page load performance
product images used eager loading unnescessary
unneccesary third party libraies where loaded
revew rendered large no of Dom nodes at only once
memory leaks caused by unbounded arrays

#changes made in index.html

removed duplicate Jquery dependencies
fixed unneccesary polyfill loading
added defer to js files where apporiated
changed below the fold product images to lazy loading

#changes made in javascript files(analitics,app and quickview)

fixed mouse trail memory leak
prevented duplicate resize event listerner
reduce layut thrashing
improved animation performance
fixed quick vies model  memory leak
removed unneccesary document level event listeners

#css
removed unneccesary will change usage
optimize render performace

#lighthouse result

##before optimization 
performance 35 
accessability 82
best pracice 79
seo 91 

##after optimization

performance 92
accessability 98
best pracice 100
seo 100