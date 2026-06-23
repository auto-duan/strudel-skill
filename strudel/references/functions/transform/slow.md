---
name: slow
category: transform
signature: "slow(factor: number | Pattern): Pattern"
aliases: []
tags: [time, tempo, slow, stretch, cycles]
related: [fast, hurry, cpm]
source: https://strudel.cc/learn/time-modifiers/
status: verified
---

Slow down a pattern over the given number of cycles, like the "/" operator in mini notation.

## Parameters
- `factor` (number | Pattern) — how many cycles to stretch the pattern over

## Returns
Pattern — the slowed-down pattern

## Examples
```js
s("bd hh sd hh").slow(2) // s("[bd hh sd hh]/2")
```

## Gotchas
- `slow(2)` is the inverse of `fast(2)`; it stretches rather than repeats.
- Equivalent to the `/` operator in mini notation.

## See also
- `fast` — speeds a pattern up (inverse of `slow`)
- `cpm` — sets tempo in cycles per minute
