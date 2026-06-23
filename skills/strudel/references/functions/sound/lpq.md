---
name: lpq
category: sound
signature: "lpq(q: number | Pattern): Pattern"
aliases: [resonance]
tags: [sound, filter, lowpass, resonance]
related: [lpf, hpq, bpq]
source: https://strudel.cc/learn/effects/
status: verified
---

Controls the low-pass filter q-value (resonance), emphasizing frequencies near the cutoff.

## Parameters
- `q` (number | Pattern) — resonance / Q value, `0` to `50`.

## Returns
Pattern — the pattern with low-pass resonance applied.

## Examples
```js
// from official docs
s("bd sd [~ bd] sd,hh*8").lpf(2000).lpq("<0 10 20 30>")
// increasingly resonant peak at the cutoff
```

## Gotchas
- Has no audible effect without a `lpf` cutoff set.
- High Q values create a sharp resonant peak that can be loud near the cutoff frequency.

## See also
- `lpf` — sets the low-pass cutoff frequency.
- `hpq` — resonance for the high-pass filter.
