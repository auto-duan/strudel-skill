---
name: loopEnd
category: sound
signature: "loopEnd(position: number | Pattern): Pattern"
aliases: [loope]
tags: [sound, sample, playback, loop]
related: [loop, loopBegin, end]
source: https://strudel.cc/learn/samples/
status: verified
---

Sets the point at which the looping section of a sample ends.

## Parameters
- `position` (number | Pattern) — normalized end of the loop, `0` to `1`. Must fall between `begin` and `end`, and after `loopBegin`.

## Returns
Pattern — the pattern with the loop end point set.

## Examples
```js
// from official docs
s("space").loop(1).loopEnd("<1 .75 .5 .25>")._scope()
// shrinks the looping section each cycle
```

## Gotchas
- Has no effect unless `loop(1)` is active.
- Must be after `loopBegin` and within the `begin`/`end` window.

## See also
- `loop` — enables sample looping.
- `loopBegin` — the start of the looping section.
