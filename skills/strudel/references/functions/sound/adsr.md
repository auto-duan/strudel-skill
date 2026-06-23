---
name: adsr
category: sound
signature: "adsr(\"attack:decay:sustain:release\" | Pattern): Pattern"
aliases: []
tags: [sound, envelope, adsr, amplitude]
related: [attack, decay, sustain, release]
source: https://strudel.cc/learn/effects/
status: verified
---

Sets the full amplitude envelope (Attack, Decay, Sustain, Release) in a single call.

## Parameters
- `attack` (number | Pattern) — attack time in seconds.
- `decay` (number | Pattern) — decay time in seconds.
- `sustain` (number | Pattern) — sustain level, `0` to `1`.
- `release` (number | Pattern) — release time in seconds.

Typically written as a colon-separated string: `adsr(".1:.1:.5:.2")`.

## Returns
Pattern — the pattern with the full ADSR envelope applied.

## Examples
```js
// from official docs
note("[c3 bb2 f3 eb3]*2").sound("sawtooth").lpf(600).adsr(".1:.1:.5:.2")
// attack .1s, decay .1s, sustain .5, release .2s
```

## Gotchas
- Order is attack, decay, sustain, release — sustain is the only *level* (0–1); the other three are times in seconds.
- Equivalent to chaining `.attack(.1).decay(.1).sustain(.5).release(.2)`.

## See also
- `attack` / `decay` / `sustain` / `release` — the individual envelope stages.
