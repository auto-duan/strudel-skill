---
name: delaytime
category: sound
signature: "delaytime(seconds: number | Pattern): Pattern"
aliases: [delayt, dt]
tags: [sound, delay, echo, effect]
related: [delay, delayfeedback]
source: https://strudel.cc/learn/effects/
status: verified
---

Sets the time of the delay effect, in seconds.

## Parameters
- `seconds` (number | Pattern) — delay time in seconds.

## Returns
Pattern — the pattern with the delay time set.

## Examples
```js
// from official docs
note("d d a# a".fast(2)).s("sawtooth").delay(.8).delaytime(1/2).delayspeed("<2 .5 -1 -2>")
// half-second echoes whose speed is modulated
```

## Gotchas
- The delay time is in seconds and is not synced to cycle tempo by default.
- Has no effect unless `delay` level is greater than 0.

## See also
- `delay` — sets the delay send level.
- `delayfeedback` — sets the feedback amount.
