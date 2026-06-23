---
name: begin
category: sound
signature: "begin(position: number | Pattern): Pattern"
aliases: []
tags: [sound, sample, playback, trim]
related: [end, loop, loopBegin, speed]
source: https://strudel.cc/learn/samples/
status: verified
---

Starts sample playback at a designated point within the sample.

## Parameters
- `position` (number | Pattern) — normalized start position, `0` (very start) to `1` (very end).

## Returns
Pattern — the pattern starting playback at the given offset.

## Examples
```js
// signature/range from official docs (samples page lists no example for begin)
s("rave").begin("<0 .25 .5 .75>")
// starts the sample 0, 1/4, 1/2, 3/4 of the way in
```

## Gotchas
- Position is normalized `0`–`1`, not in seconds or samples.
- `begin` must be before `end`; pairing them lets you play an arbitrary slice of a sample.

## See also
- `end` — sets where playback stops.
- `loopBegin` — start point of the looping section when `loop` is on.
