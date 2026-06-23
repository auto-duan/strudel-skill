---
name: sometimesBy
category: transform
signature: "sometimesBy(probability: number, f: Pattern => Pattern): Pattern"
aliases: []
tags: [random, conditional, probability, transform]
related: [sometimes, often, rarely, someCyclesBy]
source: https://strudel.cc/learn/random-modifiers/
status: verified
---

Randomly applies the given function to events by the given probability.

## Parameters
- `probability` (number | Pattern) — the chance, between 0 and 1, that the function is applied to each event.
- `f` (function) — the transformation to apply, e.g. `x => x.speed("0.5")`.

## Returns
Pattern — the pattern with `f` applied to a random subset of events selected per the probability.

## Examples
```js
// from official docs
s("hh*8").sometimesBy(.4, x=>x.speed("0.5"))
```

## Gotchas
- The decision is made per event, not per cycle — use `someCyclesBy` to decide once per cycle instead.
- `sometimes`, `often`, `rarely`, `almostNever`, `almostAlways`, `always` and `never` are shorthands for specific probabilities.

## See also
- `sometimes` — shorthand for `sometimesBy(0.5, f)`
- `someCyclesBy` — applies the decision per cycle rather than per event
