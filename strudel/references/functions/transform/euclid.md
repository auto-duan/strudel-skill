---
name: euclid
category: transform
signature: "euclid(pulses: number, steps: number): Pattern"
aliases: []
tags: [rhythm, euclidean, structure]
related: [euclidRot, euclidLegato, ply]
source: https://strudel.cc/learn/time-modifiers/
status: verified
---

Changes the structure of a pattern into a Euclidean rhythm: distributes `pulses` pulses as evenly as possible across `steps` steps.

## Parameters
- `pulses` (number) — number of sounding pulses.
- `steps` (number) — total number of steps (how many equal slots one cycle is divided into).

## Returns
Pattern — the pattern triggered on the Euclidean distribution.

## Examples
```js
note("c3").euclid(3,8)
// 3 pulses across 8 steps: the classic tresillo / "Pop Clave"
```

## Gotchas
- `euclid(3,8)` is equivalent to `"c3(3,8)"` in mini-notation.
- For a rotation offset use `euclidRot(pulses, steps, rotation)`; for pulses held until the next one (no gaps) use `euclidLegato`.
- First arg is pulses, second is total steps; swapping them gives a completely different rhythm.

## See also
- `euclidRot` — Euclidean with a rotation offset.
- `euclidLegato` — each pulse sustains to the next, no gaps.
