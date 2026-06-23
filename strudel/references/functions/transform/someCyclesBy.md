---
name: someCyclesBy
category: transform
signature: "someCyclesBy(probability: number, f: Pattern => Pattern): Pattern"
aliases: [somecyclesBy]
tags: [random, conditional, probability, cycle, transform]
related: [someCycles, sometimesBy, every]
source: https://strudel.cc/learn/random-modifiers/
status: verified
---

Randomly applies the given function on a cycle-by-cycle basis, by the given probability.

## Parameters
- `probability` (number | Pattern) — the chance, between 0 and 1, that the function is applied to a whole cycle.
- `f` (function) — the transformation to apply, e.g. `x => x.speed("0.5")`.

## Returns
Pattern — the pattern with `f` applied to a random subset of whole cycles.

## Examples
```js
// from official docs
s("bd,hh*8").someCyclesBy(.3, x=>x.speed("0.5"))
```

## Gotchas
- The decision is made once per cycle, so all events in a chosen cycle are transformed together — unlike `sometimesBy`, which decides per event.

## See also
- `someCycles` — shorthand for `someCyclesBy(0.5, f)`
- `sometimesBy` — decides per event instead of per cycle
