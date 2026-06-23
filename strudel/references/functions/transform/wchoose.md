---
name: wchoose
category: transform
signature: "wchoose(...pairs: [any, number][]): Pattern"
aliases: []
tags: [random, selection, weighted, continuous, transform]
related: [choose, wchooseCycles, chooseCycles]
source: https://strudel.cc/learn/random-modifiers/
status: verified
---

Chooses randomly from the given list of elements by giving a probability (weight) to each element.

## Parameters
- `...pairs` (array) — each argument is a `[value, weight]` array; higher weights are chosen more often.

## Returns
Pattern — a continuous, weighted random selection among the given elements.

## Examples
```js
// from official docs
note("c2 g2!2 d2 f1").s(wchoose(["sine",10], ["triangle",1], ["bd:6",1]))
```

## Gotchas
- Each argument must be a `[value, weight]` pair, not a bare value (that is `choose`).
- Like `choose`, it is continuous and is sampled by the surrounding structure.
- To weight picks per cycle instead of continuously, use `wchooseCycles`.

## See also
- `choose` — unweighted (equal probability) version
- `wchooseCycles` — weighted pick, once per cycle
