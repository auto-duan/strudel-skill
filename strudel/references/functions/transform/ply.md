---
name: ply
category: transform
signature: "ply(n: number | Pattern): Pattern"
aliases: []
tags: [repeat, subdivision, structure]
related: [fast, segment, euclid]
source: https://strudel.cc/learn/time-modifiers/
status: verified
---

Repeats **each event** n times (subdividing within that event's original duration).

## Parameters
- `n` (number | Pattern) — how many times to repeat each event. Can be a pattern to vary per cycle.

## Returns
Pattern — the pattern with each event subdivided/repeated.

## Examples
```js
// each drum hit is repeated, count cycles through 1/2/3
s("bd ~ sd cp").ply("<1 2 3>")
```

## Gotchas
- Differs from `fast`: `fast(n)` repeats the **whole** pattern, `ply(n)` repeats **each event** (like turning each event into `event*n`).
- To repeat different events by different counts, pass `n` as a mini-notation pattern.

## See also
- `fast` — repeats the whole pattern, not single events.
- `segment` — samples a continuous signal into n events; different purpose.
