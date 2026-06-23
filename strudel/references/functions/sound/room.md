---
name: room
category: sound
signature: "room(level: number | Pattern): Pattern"
aliases: []
tags: [sound, reverb, effect, space]
related: [roomsize, roomlp, roomfade, roomdim, iresponse]
source: https://strudel.cc/learn/effects/
status: verified
---

Sets the level of reverb.

## Parameters
- `level` (number | Pattern) — reverb send level, `0` to `1`. Accepts optional `:size` to also set room size (e.g. `room("0.8:2")`).

## Returns
Pattern — the pattern with reverb applied.

## Examples
```js
// from official docs
s("bd sd [~ bd] sd").room("<0 .2 .4 .6 .8 1>")
// gradually increases reverb amount each cycle
```

## Gotchas
- `room` only sets the wet level; use `roomsize` (alias `rsize`/`sz`/`size`) to change the perceived space size.

## See also
- `roomsize` — sets the room size of the reverb (0–10).
- `roomlp` — reverb lowpass starting frequency.
- `iresponse` — use a sample as the impulse response for the reverb.
