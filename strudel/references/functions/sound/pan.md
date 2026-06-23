---
name: pan
category: sound
signature: "pan(position: number | Pattern): Pattern"
aliases: []
tags: [sound, stereo, panning, spatial]
related: [jux, juxBy, gain, orbit]
source: https://strudel.cc/learn/effects/
status: verified
---

Sets the position in the stereo field, from left to right.

## Parameters
- `position` (number | Pattern) — stereo position, `0` = full left, `1` = full right (`0.5` = center).

## Returns
Pattern — the pattern positioned in the stereo field.

## Examples
```js
// from official docs
s("[bd hh]*2").pan("<.5 1 .5 0>")
// moves events across the stereo image each cycle
```

## Gotchas
- Range is `0` to `1`, not `-1` to `1`. Center is `0.5`.

## See also
- `jux` — applies a function to only the right channel for stereo effects.
- `juxBy` — like `jux` but with an adjustable stereo width.
