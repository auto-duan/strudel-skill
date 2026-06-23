---
name: brandBy
category: signal
signature: "brandBy(probability: number): Pattern"
aliases: []
tags: [signal, random, continuous, binary, lfo]
related: [brand, rand]
source: https://strudel.cc/learn/signals/
status: verified
---

A continuous binary random pattern with a given probability of the value being 1.

## Parameters
- `probability` (number) — value between 0 and 1 giving the chance that each sample is 1.

## Returns
Pattern — a continuous pattern producing random binary values (0 or 1) weighted by `probability`.

## Examples
```js
s("hh*10").pan(brandBy(0.2))
```

## Gotchas
- `brandBy(0.5)` is equivalent to `brand`.
- The probability controls how often `1` appears: lower values mean mostly 0s.

## See also
- `brand` — binary random with equal (0.5) probability
- `rand` — continuous random floats between 0 and 1
