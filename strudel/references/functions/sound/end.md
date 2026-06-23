---
name: end
category: sound
signature: "end(position: number | Pattern): Pattern"
aliases: []
tags: [sound, sample, playback, trim]
related: [begin, loop, loopEnd, speed]
source: https://strudel.cc/learn/samples/
status: verified
---

Cuts off the end of each sample, setting where playback stops.

## Parameters
- `position` (number | Pattern) — normalized end position, `0` to `1` (where `1` = full sample length).

## Returns
Pattern — the pattern with the sample end trimmed.

## Examples
```js
// from official docs
s("bd*2,oh*4").end("<.1 .2 .5 1>").fast(2)
// shortens the played portion of the samples
```

## Gotchas
- Position is normalized `0`–`1`, not seconds.
- `end` must be after `begin`; use both to play an arbitrary slice.

## See also
- `begin` — sets where playback starts.
- `loopEnd` — end point of the looping section when `loop` is on.
