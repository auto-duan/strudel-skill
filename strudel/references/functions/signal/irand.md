---
name: irand
category: signal
signature: "irand(n: number): Pattern"
aliases: []
tags: [signal, random, continuous, integer, lfo]
related: [rand, perlin, brand]
source: https://strudel.cc/learn/signals/
status: verified
---

A continuous pattern of random integers between 0 and n-1.

## Parameters
- `n` (number) — the exclusive upper bound; values returned are integers in the range 0 to n-1.

## Returns
Pattern — a continuous pattern producing random integers from 0 to n-1.

## Examples
```js
n(irand(8)).struct("x x*2 x x*3")
```

## Gotchas
- Unlike `rand`, `irand` takes an argument `n` and returns whole integers, not fractional values.
- As a continuous signal it is usually sampled via `.struct(...)` or `.segment(n)` to produce discrete events.
- The upper bound is exclusive: `irand(8)` yields 0..7, never 8.

## See also
- `rand` — random floats between 0 and 1
- `perlin` — smooth (correlated) random noise
