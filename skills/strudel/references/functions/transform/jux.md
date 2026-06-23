---
name: jux
category: transform
signature: "jux(f: Pattern => Pattern): Pattern"
aliases: []
tags: [stereo, panning, conditional, transform]
related: [juxBy, superimpose, layer]
source: https://strudel.cc/learn/effects/
status: verified
---

Creates stereo effects by applying a function to a pattern, but only in the right-hand channel.

## Parameters
- `f` (function) — a function that takes a pattern and returns a transformed pattern, applied only to the right channel (the left channel keeps the original).

## Returns
Pattern — the original pattern panned left, stacked with the transformed copy panned right.

## Examples
```js
// from official docs
s("bd lt [~ ht] mt cp ~ bd hh").jux(rev)
// the right channel plays the reversed pattern, the left channel the original
```

## Gotchas
- `jux` takes a function, not a control pattern. To use a control pattern, wrap it: `jux(x => x.speed(2))`.
- It always produces full stereo separation (mono left, transformed right); use `juxBy` for partial width.

## See also
- `juxBy` — like `jux` but with adjustable stereo width (0 = mono, 1 = full stereo)
- `superimpose` — layers a transformed copy without splitting it across channels
