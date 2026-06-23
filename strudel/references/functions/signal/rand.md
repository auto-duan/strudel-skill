---
name: rand
category: signal
signature: "rand: Pattern"
aliases: []
tags: [signal, random, continuous, noise, lfo]
related: [irand, perlin, brand, rand2]
source: https://strudel.cc/learn/signals/
status: verified
---

A continuous pattern of random numbers between 0 and 1.

## Parameters
None — `rand` is a continuous signal (no arguments).

## Returns
Pattern — a continuous pattern producing random values from 0 to 1.

## Examples
```js
s("bd*4,hh*8").cutoff(rand.range(500,8000))
```

## Gotchas
- As a continuous signal it must be sampled (e.g. with `.segment(n)`) to produce discrete events, but it can also be fed directly into continuous controls like `cutoff` or `pan`.
- Use `.range(min, max)` to remap the default 0..1 output to another range.
- A `rand2` variant exists that outputs over the -1..1 range instead of 0..1.
- Unlike `perlin`, `rand` is uncorrelated noise — consecutive samples have no smooth relationship.

## See also
- `irand` — random integers between 0 and n-1
- `perlin` — smooth (correlated) random noise
- `brand` — random binary (0 or 1) signal
