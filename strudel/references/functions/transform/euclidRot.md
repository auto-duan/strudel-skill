---
name: euclidRot
category: transform
signature: "euclidRot(pulses: number, steps: number, rotation: number): Pattern"
aliases: []
tags: [rhythm, euclidean, structure, rotation]
related: [euclid, euclidLegato]
source: https://strudel.cc/learn/time-modifiers/
status: verified
---

Like `euclid`, but has an additional parameter for "rotating" the resulting sequence.

## Parameters
- `pulses` (number) — number of onsets / pulses
- `steps` (number) — number of steps to fill
- `rotation` (number) — amount to rotate the resulting sequence

## Returns
Pattern — the rotated Euclidean rhythm pattern

## Examples
```js
note("c3").euclidRot(3,16,14)
```

## Gotchas
- Identical to `euclid` except for the third `rotation` argument that shifts where the pulses land.

## See also
- `euclid` — Euclidean rhythm without rotation
- `euclidLegato` — Euclidean rhythm where each pulse is held until the next
