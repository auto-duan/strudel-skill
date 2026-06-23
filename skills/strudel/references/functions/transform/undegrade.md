---
name: undegrade
category: transform
signature: "undegrade(): Pattern"
aliases: []
tags: [random, conditional, probability, thinning, transform]
related: [degrade, undegradeBy, degradeBy]
source: https://strudel.cc/learn/random-modifiers/
status: verified
---

Inverse of `degrade`: randomly removes 50% of events using the inverse random selection.

## Parameters
None.

## Returns
Pattern — the pattern with roughly half of its events removed (the half `degrade` would keep).

## Examples
```js
// from official docs
s("hh*8").undegrade()
```

## Gotchas
- Shorthand for `undegradeBy(0.5)`.
- `degrade` and `undegrade` remove complementary halves, so layering both copies reconstructs the full pattern split across two random halves.

## See also
- `degrade` — the non-inverted version
- `undegradeBy` — remove a custom (inverted) fraction of events
