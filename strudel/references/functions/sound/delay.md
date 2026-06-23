---
name: delay
category: sound
signature: "delay(level: number | Pattern): Pattern"
aliases: []
tags: [sound, delay, echo, effect]
related: [delaytime, delayfeedback, room, orbit]
source: https://strudel.cc/learn/effects/
status: verified
---

Sets the level of the delay (echo) signal.

## Parameters
- `level` (number | Pattern) — delay send level, `0` to `1`. Accepts optional `:delaytime:delayfeedback` (e.g. `delay("0.5:0.25:0.8")`).

## Returns
Pattern — the pattern with delay applied.

## Examples
```js
// from official docs
s("bd bd").delay("<0 .25 .5 1>")
// increases the echo level each cycle
```

## Gotchas
- The colon form packs three controls into one string: `delay("level:time:feedback")`.
- Combine with `orbit` to give different patterns independent delay buses.

## See also
- `delaytime` — sets the delay time in seconds.
- `delayfeedback` — sets how much delayed signal is fed back.
