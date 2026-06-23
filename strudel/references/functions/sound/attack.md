---
name: attack
category: sound
signature: "attack(time: number | Pattern): Pattern"
aliases: [att]
tags: [sound, envelope, adsr, amplitude]
related: [decay, sustain, release, adsr]
source: https://strudel.cc/learn/effects/
status: verified
---

Amplitude envelope attack time: how long it takes for the sound to reach peak level after it starts.

## Parameters
- `time` (number | Pattern) — attack time in seconds.

## Returns
Pattern — the pattern with the attack stage set.

## Examples
```js
// from official docs
note("c3 e3 f3 g3").attack("<0 .1 .5>")
// from instant onset to a slow fade-in
```

## Gotchas
- A longer attack softens transients; `0` gives an instant onset (good for percussion).
- Part of the ADSR amplitude envelope; combine with `decay`, `sustain`, `release` or set all four at once with `adsr`.

## See also
- `decay` — time from peak down to the sustain level.
- `adsr` — set attack, decay, sustain, release together.
