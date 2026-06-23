---
name: loopBegin
category: sound
signature: "loopBegin(position: number | Pattern): Pattern"
aliases: [loopb]
tags: [sound, sample, playback, loop]
related: [loop, loopEnd, begin]
source: https://strudel.cc/learn/samples/
status: verified
---

Sets the point at which the looping section of a sample begins.

## Parameters
- `position` (number | Pattern) — normalized start of the loop, `0` to `1`. Must fall between `begin` and `end`, and before `loopEnd`.

## Returns
Pattern — the pattern with the loop start point set.

## Examples
```js
// from official docs
s("space").loop(1).loopBegin("<0 .125 .25>")._scope()
// moves the loop's start point each cycle
```

## Gotchas
- Has no effect unless `loop(1)` is active.
- Must be before `loopEnd` and within the `begin`/`end` window.

## See also
- `loop` — enables sample looping.
- `loopEnd` — the end of the looping section.
