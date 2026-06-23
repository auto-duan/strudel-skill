---
name: square
category: signal
signature: "square: Pattern"
aliases: []
tags: [signal, continuous, oscillator, lfo, square]
related: [sine, saw, tri, cosine]
source: https://strudel.cc/learn/signals/
status: verified
---

A square signal that alternates continuously between 0 and 1.

## Parameters
None — `square` is a continuous signal (no arguments).

## Returns
Pattern — a continuous pattern producing values of 0 or 1 (the square wave).

## Examples
```js
n(square.segment(4).range(0,7))
```

## Gotchas
- As a continuous signal it must be sampled with `.segment(n)` to produce discrete events.
- Use `.range(min, max)` to remap the default 0..1 output to another range.
- A `square2` variant exists that outputs over the -1..1 range instead of 0..1.
- Different from `brand`: `square` is a deterministic alternating wave, `brand` is random 0/1.

## See also
- `sine` — sine signal
- `tri` — triangle signal
- `brand` — random binary (0 or 1) signal
