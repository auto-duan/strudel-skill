---
name: often
category: transform
signature: "often(f: Pattern => Pattern): Pattern"
aliases: []
tags: [random, conditional, probability, transform]
related: [sometimesBy, sometimes, rarely, almostAlways]
source: https://strudel.cc/learn/random-modifiers/
status: verified
---

Applies the given function to events most of the time (75% chance).

## Parameters
- `f` (function) — the transformation to apply, e.g. `x => x.speed("0.5")`.

## Returns
Pattern — the pattern with `f` applied to about three quarters of its events at random.

## Examples
```js
// from official docs
s("hh*8").often(x=>x.speed("0.5"))
```

## Gotchas
- Shorthand for `sometimesBy(0.75, f)`.

## See also
- `sometimes` — 50% chance
- `almostAlways` — 90% chance
- `rarely` — 25% chance
