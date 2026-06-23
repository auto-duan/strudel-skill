---
name: tri
category: signal
signature: "tri: Pattern"
aliases: []
tags: [signal, continuous, oscillator, lfo, triangle]
related: [sine, saw, square, cosine]
source: https://strudel.cc/learn/signals/
status: verified
---

A triangle signal that oscillates continuously between 0 and 1.

## Parameters
None — `tri` is a continuous signal (no arguments).

## Returns
Pattern — a continuous pattern producing values from 0 to 1.

## Examples
```js
n(tri.segment(8).range(0,7))
```

## Gotchas
- As a continuous signal it must be sampled with `.segment(n)` to produce discrete events.
- Use `.range(min, max)` to remap the default 0..1 output to another range.
- A `tri2` variant exists that outputs over the -1..1 range instead of 0..1.

## See also
- `sine` — sine signal
- `saw` — sawtooth signal
- `square` — square signal
