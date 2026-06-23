---
name: bpq
category: sound
signature: "bpq(q: number | Pattern): Pattern"
aliases: [bandq]
tags: [sound, filter, bandpass, resonance]
related: [bpf, lpq, hpq]
source: https://strudel.cc/learn/effects/
status: verified
---

Sets the band-pass q-factor (resonance), controlling the width of the passed band.

## Parameters
- `q` (number | Pattern) — Q-factor / resonance.

## Returns
Pattern — the pattern with band-pass resonance applied.

## Examples
```js
// from official docs
s("bd sd [~ bd] sd").bpf(500).bpq("<0 1 2 3>")
// narrows the passed band as Q increases
```

## Gotchas
- Has no audible effect without a `bpf` center frequency set.
- Higher Q narrows the band (more selective / resonant).

## See also
- `bpf` — sets the band-pass center frequency.
- `lpq` / `hpq` — resonance for low-pass and high-pass filters.
