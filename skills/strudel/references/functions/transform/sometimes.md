---
name: sometimes
category: transform
signature: "sometimes(f: Pattern => Pattern): Pattern"
aliases: []
tags: [random, conditional, probability, transform]
related: [sometimesBy, often, rarely, someCycles]
source: https://strudel.cc/learn/random-modifiers/
status: verified
---

Applies the given function to events with a 50% chance.

## Parameters
- `f` (function) — the transformation to apply, e.g. `x => x.speed("0.5")`.

## Returns
Pattern — the pattern with `f` applied to roughly half of its events at random.

## Examples
```js
// from official docs
s("hh*8").sometimes(x=>x.speed("0.5"))
```

## Gotchas
- Shorthand for `sometimesBy(0.5, f)`.
- The decision is per event; use `someCycles` to decide once per cycle.

## See also
- `sometimesBy` — set an explicit probability
- `often` — shorthand for `sometimesBy(0.75, f)`
- `rarely` — shorthand for `sometimesBy(0.25, f)`
