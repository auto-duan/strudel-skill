---
name: sine
category: signal
signature: "sine: Pattern"
aliases: []
tags: [signal, continuous, oscillator, lfo, sine]
related: [cosine, saw, tri, square]
source: https://strudel.cc/learn/signals/
status: verified
---

Sine signal that oscillates continuously between 0 and 1.

## Parameters
None — `sine` is a continuous signal (no arguments).

## Returns
Pattern — a continuous pattern producing values from 0 to 1.

## Examples
```js
n(sine.segment(16).range(0,15)).scale("C:minor")
```

## Gotchas
- As a continuous signal it must be sampled with `.segment(n)` to produce discrete events.
- Use `.range(min, max)` to remap the default 0..1 output to another range.
- A `sine2` variant exists that outputs over the -1..1 range instead of 0..1.

## See also
- `cosine` — sine offset by a quarter phase
- `tri` — triangle signal
- `saw` — sawtooth signal
