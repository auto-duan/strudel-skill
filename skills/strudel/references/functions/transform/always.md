---
name: always
category: transform
signature: "always(f: Pattern => Pattern): Pattern"
aliases: []
tags: [random, conditional, probability, transform]
related: [sometimesBy, almostAlways, never]
source: https://strudel.cc/learn/random-modifiers/
status: verified
---

Applies the given function to every event (100% chance).

## Parameters
- `f` (function) — the transformation to apply, e.g. `x => x.speed("0.5")`.

## Returns
Pattern — the pattern with `f` applied to all events.

## Examples
```js
// from official docs
s("hh*8").always(x=>x.speed("0.5"))
```

## Gotchas
- Shorthand for `sometimesBy(1, f)` — the function is always called.
- Mostly useful as the endpoint of the probability family or when the probability is patterned.

## See also
- `never` — 0% chance (function is never applied)
- `almostAlways` — 90% chance
