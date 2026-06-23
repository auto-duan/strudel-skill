---
name: brand
category: signal
signature: "brand: Pattern"
aliases: []
tags: [signal, random, continuous, binary, lfo]
related: [brandBy, rand, square]
source: https://strudel.cc/learn/signals/
status: verified
---

A continuous pattern of 0 or 1 (binary random).

## Parameters
None — `brand` is a continuous signal (no arguments).

## Returns
Pattern — a continuous pattern producing random binary values (0 or 1).

## Examples
```js
s("hh*10").pan(brand)
```

## Gotchas
- `brand` is random binary noise — different from `square`, which is a deterministic alternating wave.
- By default each value is equally likely to be 0 or 1; use `brandBy` to set a custom probability.

## See also
- `brandBy` — binary random with a configurable probability of being 1
- `rand` — continuous random floats between 0 and 1
