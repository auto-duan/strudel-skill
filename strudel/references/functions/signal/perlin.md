---
name: perlin
category: signal
signature: "perlin: Pattern"
aliases: []
tags: [signal, random, continuous, noise, perlin, lfo]
related: [rand, irand, sine]
source: https://strudel.cc/learn/signals/
status: verified
---

A continuous pattern of perlin noise in the range 0..1.

## Parameters
None — `perlin` is a continuous signal (no arguments).

## Returns
Pattern — a continuous pattern producing smooth random values from 0 to 1.

## Examples
```js
s("bd*4,hh*8").cutoff(perlin.range(500,8000))
```

## Gotchas
- Unlike `rand`, perlin noise is smooth/correlated — consecutive values change gradually rather than jumping randomly, making it well suited to organic modulation.
- As a continuous signal it can be sampled with `.segment(n)` or fed directly into continuous controls.
- Use `.range(min, max)` to remap the default 0..1 output to another range.

## See also
- `rand` — uncorrelated random noise (0 to 1)
- `sine` — smooth deterministic oscillation
