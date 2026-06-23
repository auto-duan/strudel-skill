---
name: rarely
category: transform
signature: "rarely(f: Pattern => Pattern): Pattern"
aliases: []
tags: [random, conditional, probability, transform]
related: [sometimesBy, sometimes, often, almostNever]
source: https://strudel.cc/learn/random-modifiers/
status: verified
---

Applies the given function to events occasionally (25% chance).

## Parameters
- `f` (function) — the transformation to apply, e.g. `x => x.speed("0.5")`.

## Returns
Pattern — the pattern with `f` applied to about one quarter of its events at random.

## Examples
```js
// from official docs
s("hh*8").rarely(x=>x.speed("0.5"))
```

## Gotchas
- Shorthand for `sometimesBy(0.25, f)`.

## See also
- `sometimes` — 50% chance
- `often` — 75% chance
- `almostNever` — 10% chance
