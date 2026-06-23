---
name: degradeBy
category: transform
signature: "degradeBy(amount: number): Pattern"
aliases: []
tags: [random, conditional, probability, thinning, transform]
related: [degrade, undegradeBy, undegrade, sometimesBy]
source: https://strudel.cc/learn/random-modifiers/
status: verified
---

Randomly removes events from the pattern by a given amount.

## Parameters
- `amount` (number) — value between 0 and 1 giving the fraction of events to remove.

## Returns
Pattern — the pattern with a random subset of its events dropped.

## Examples
```js
// from official docs
s("hh*8").degradeBy(0.2)
```

## Gotchas
- `degradeBy` removes events; it does not transform them — use `sometimesBy` to apply a function instead.
- `undegradeBy` uses the inverse random selection, so `degradeBy(x)` and `undegradeBy(x)` remove complementary events.

## See also
- `degrade` — shorthand for `degradeBy(0.5)`
- `undegradeBy` — inverse selection (keeps what `degradeBy` would remove)
