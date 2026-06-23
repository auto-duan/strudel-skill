---
name: roomsize
category: sound
signature: "roomsize(size: number | Pattern): Pattern"
aliases: [rsize, sz, size]
tags: [sound, reverb, effect, space]
related: [room, roomlp, roomfade, roomdim]
source: https://strudel.cc/learn/effects/
status: verified
---

Sets the room size of the reverb.

## Parameters
- `size` (number | Pattern) — reverb room size, `0` to `10`.

## Returns
Pattern — the pattern with the reverb room size set.

## Examples
```js
// from official docs
s("bd sd [~ bd] sd").room(.8).rsize(1)
// adds reverb with a small room size
```

## Gotchas
- Has no audible effect without a non-zero `room` level set first.
- Aliases `sz` and `size` are short forms; `size` may shadow other readers — prefer `rsize` for clarity.

## See also
- `room` — sets the level (wet amount) of the reverb.
- `roomlp` — reverb lowpass starting frequency.
