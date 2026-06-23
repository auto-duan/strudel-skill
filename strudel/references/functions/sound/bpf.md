---
name: bpf
category: sound
signature: "bpf(frequency: number | Pattern): Pattern"
aliases: [bandf, bp]
tags: [sound, filter, bandpass, eq]
related: [bpq, lpf, hpf]
source: https://strudel.cc/learn/effects/
status: verified
---

Sets the center frequency of the band-pass filter, passing a band of frequencies around the center.

## Parameters
- `frequency` (number | Pattern) — center frequency in Hz. Accepts an optional `:bpq` value (e.g. `bpf("500:2")`).

## Returns
Pattern — the filtered pattern.

## Examples
```js
// from official docs
s("bd sd [~ bd] sd,hh*6").bpf("<1000 2000 4000 8000>")
// isolates a moving band of frequencies
```

## Gotchas
- Passes only frequencies near the center, attenuating both lows and highs.
- The colon form sets the Q: `bpf("500:2")` is `bpf(500).bpq(2)`.

## See also
- `bpq` — band-pass Q-factor (resonance / bandwidth).
- `lpf` / `hpf` — low-pass and high-pass filters.
