---
name: clip
category: transform
signature: "clip(factor: number | Pattern): Pattern"
aliases: [legato]
tags: [time, duration, legato, gate, sustain]
related: [euclidLegato, ply, segment]
source: https://strudel.cc/learn/time-modifiers/
status: verified
---

Multiplies the duration of each event with the given number, also cutting samples off at the end if they exceed the duration.

## Parameters
- `factor` (number | Pattern) — multiplier for the event duration (factor >= 0)

## Returns
Pattern — the pattern with modified event durations

## Examples
```js
note("c a f e").s("piano").clip("<.5 1 2>")
```

## Gotchas
- `clip` is also available under the alias `legato`.
- Values below 1 shorten events (more staccato); values above 1 lengthen/overlap them (more legato).
- Samples are cut off at the end if they exceed the new duration.

## See also
- `euclidLegato` — holds each Euclidean pulse until the next so there are no gaps
- `ply` — repeats each event a number of times
