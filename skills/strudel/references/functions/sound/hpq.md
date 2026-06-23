---
name: hpq
category: sound
signature: "hpq(q: number | Pattern): Pattern"
aliases: [hresonance]
tags: [sound, filter, highpass, resonance]
related: [hpf, lpq, bpq]
source: https://strudel.cc/learn/effects/
status: verified
---

Controls the high-pass filter q-value (resonance).

## Parameters
- `q` (number | Pattern) — resonance / Q value, `0` to `50`.

## Returns
Pattern — the pattern with high-pass resonance applied.

## Examples
```js
// from official docs
s("bd sd [~ bd] sd,hh*8").hpf(2000).hpq("<0 10 20 30>")
// adds an increasingly resonant peak at the high-pass cutoff
```

## Gotchas
- Has no audible effect without an `hpf` cutoff set.

## See also
- `hpf` — sets the high-pass cutoff frequency.
- `lpq` — resonance for the low-pass filter.
