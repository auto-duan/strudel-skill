---
name: delayfeedback
category: sound
signature: "delayfeedback(feedback: number | Pattern): Pattern"
aliases: [delayfb, dfb]
tags: [sound, delay, echo, effect, feedback]
related: [delay, delaytime]
source: https://strudel.cc/learn/effects/
status: verified
---

Sets the level of the signal that is fed back into the delay, controlling how many repeats are heard.

## Parameters
- `feedback` (number | Pattern) — feedback amount, `0` to just under `1`.

## Returns
Pattern — the pattern with delay feedback set.

## Examples
```js
// from official docs
s("bd").delay(.25).delayfeedback("<.25 .5 .75 1>")
// more repeats as feedback rises
```

## Gotchas
- A value of `1` (or above) creates a self-sustaining feedback loop that never decays — it can build up and get very loud.
- Has no effect unless `delay` level is greater than 0.

## See also
- `delay` — sets the delay send level.
- `delaytime` — sets the delay time in seconds.
