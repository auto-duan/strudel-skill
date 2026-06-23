---
name: juxBy
category: transform
signature: "juxBy(width: number, f: Pattern => Pattern): Pattern"
aliases: [juxby]
tags: [stereo, panning, conditional, transform]
related: [jux, superimpose, layer]
source: https://strudel.cc/learn/effects/
status: verified
---

Like `jux`, but with adjustable stereo width where 0 is mono and 1 is full stereo.

## Parameters
- `width` (number | Pattern) — the stereo width between 0 (mono) and 1 (full stereo separation).
- `f` (function) — a function applied to the right-channel copy of the pattern.

## Returns
Pattern — the original and transformed copies spread across the stereo field by `width`.

## Examples
```js
// from official docs
s("bd lt [~ ht] mt cp ~ bd hh").juxBy("<0 .5 1>/2", rev)
// the stereo width cycles between mono and full stereo
```

## Gotchas
- `juxBy(1, f)` is equivalent to `jux(f)`; `juxBy(0, f)` collapses both copies to the center (mono).
- The first argument is the width, the second is the function — easy to swap by mistake.

## See also
- `jux` — full-stereo version (equivalent to `juxBy(1, ...)`)
- `superimpose` — layers a transformed copy without stereo placement
