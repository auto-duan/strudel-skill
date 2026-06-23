---
name: decay
category: sound
signature: "decay(time: number | Pattern): Pattern"
aliases: [dec]
tags: [sound, envelope, adsr, amplitude]
related: [attack, sustain, release, adsr]
source: https://strudel.cc/learn/effects/
status: verified
---

Amplitude envelope decay time: how long it takes, after the attack peak, to fall to the sustain level.

## Parameters
- `time` (number | Pattern) — decay time in seconds.

## Returns
Pattern — the pattern with the decay stage set.

## Examples
```js
// from official docs
note("c3 e3 f3 g3").decay("<.1 .2 .3 .4>").sustain(0)
// with sustain 0, longer decay = longer plucky tail
```

## Gotchas
- With `sustain(0)` the sound is purely attack+decay (a pluck/percussive shape).
- Part of the ADSR amplitude envelope.

## See also
- `sustain` — the level held after decay.
- `adsr` — set attack, decay, sustain, release together.
