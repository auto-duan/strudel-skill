---
name: euclidLegato
category: transform
signature: "euclidLegato(pulses: number, steps: number, rotation?, pat?): Pattern"
aliases: []
tags: [rhythm, euclidean, structure, legato, sustain]
related: [euclid, euclidRot, clip]
source: https://strudel.cc/learn/time-modifiers/
status: verified
---

Similar to `euclid`, but each pulse is held until the next pulse, so there will be no gaps.

## Parameters
- `pulses` (number) — number of onsets / pulses
- `steps` (number) — number of steps to fill
- `rotation` () — amount to rotate the resulting sequence (type not specified in docs)
- `pat` () — pattern argument (type not specified in docs)

## Returns
Pattern — the gap-free (legato) Euclidean rhythm pattern

## Examples
```js
note("c3").euclidLegato(3,8)
```

## Gotchas
- Unlike `euclid`, no gaps are left between pulses; each event is sustained until the next.
- The official signature lists `rotation` and `pat` without explicit types.

## See also
- `euclid` — Euclidean rhythm with gaps
- `euclidRot` — Euclidean rhythm with rotation
- `clip` — multiplies event durations (legato/staccato control)
