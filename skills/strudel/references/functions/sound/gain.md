---
name: gain
category: sound
signature: "gain(amount: number | Pattern): Pattern"
aliases: []
tags: [sound, dynamics, volume, amplitude]
related: [velocity, postgain, compressor, pan]
source: https://strudel.cc/learn/effects/
status: verified
---

Controls the gain by an exponential amount.

## Parameters
- `amount` (number | Pattern) — gain multiplier; applied exponentially. Unrestricted range.

## Returns
Pattern — the pattern with per-event gain applied.

## Examples
```js
// from official docs
s("hh*8").gain(".4!2 1 .4!2 1 .4 1").fast(2)
// accents some hi-hats louder than others
```

## Gotchas
- Gain is applied exponentially, so it does not map linearly to perceived loudness.
- `velocity` multiplies with `gain`; both affect amplitude. Use `postgain` to apply gain *after* effects (e.g. after a compressor).

## See also
- `velocity` — separate amplitude control (0–1) that multiplies with gain.
- `postgain` — gain applied after all effects have been processed.
