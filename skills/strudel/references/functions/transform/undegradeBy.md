---
name: undegradeBy
category: transform
signature: "undegradeBy(amount: number): Pattern"
aliases: []
tags: [random, conditional, probability, thinning, transform]
related: [degradeBy, undegrade, degrade]
source: https://strudel.cc/learn/random-modifiers/
status: verified
---

Inverse of `degradeBy`: randomly removes events by the given amount using the inverse random selection.

## Parameters
- `amount` (number) — value between 0 and 1 giving the fraction of events to remove.

## Returns
Pattern — the pattern with a random subset of its events dropped (complementary to `degradeBy`).

## Examples
```js
// from official docs
s("hh*8").undegradeBy(0.2)
```

## Gotchas
- Uses the inverse of `degradeBy`'s random decision, so combining `degradeBy(x)` and `undegradeBy(x)` on copies recovers complementary event sets — useful for splitting a pattern into two random halves.

## See also
- `degradeBy` — the non-inverted version
- `undegrade` — shorthand for `undegradeBy(0.5)`
