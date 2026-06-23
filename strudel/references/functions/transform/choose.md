---
name: choose
category: transform
signature: "choose(...xs: any[]): Pattern"
aliases: []
tags: [random, selection, continuous, transform]
related: [wchoose, chooseCycles, wchooseCycles, rand]
source: https://strudel.cc/learn/random-modifiers/
status: verified
---

Chooses randomly (continuously) from the given list of elements.

## Parameters
- `...xs` (any) — the values or patterns to choose from.

## Returns
Pattern — a continuous random selection among the given elements.

## Examples
```js
// from official docs
note("c2 g2!2 d2 f1").s(choose("sine", "triangle", "bd:6"))
```

## Gotchas
- `choose` is a continuous signal — it must be sampled (e.g. via `.segment(n)` or by feeding it into a structured context) to yield discrete picks.
- Each element has equal probability; use `wchoose` to weight them.
- To pick once per cycle instead of continuously, use `chooseCycles`.

## See also
- `wchoose` — weighted version (assign a probability to each element)
- `chooseCycles` — picks one element at random per cycle
