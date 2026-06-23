---
name: degrade
category: transform
signature: "degrade(): Pattern"
aliases: []
tags: [random, conditional, probability, thinning, transform]
related: [degradeBy, undegrade, undegradeBy]
source: https://strudel.cc/learn/random-modifiers/
status: verified
---

Randomly removes 50% of events from the pattern.

## Parameters
None.

## Returns
Pattern — the pattern with roughly half of its events removed at random.

## Examples
```js
// from official docs
s("hh*8").degrade()
```

## Gotchas
- Shorthand for `degradeBy(0.5)`.
- `degrade` and `undegrade` remove complementary halves of the events (same random source, inverse selection).

## See also
- `degradeBy` — remove a custom fraction of events
- `undegrade` — removes the opposite half that `degrade` keeps
