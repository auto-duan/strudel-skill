---
name: freq
category: sound
signature: "freq(hertz: number | Pattern): Pattern"
aliases: []
tags: [sound, pitch, frequency, synth]
related: [note, n, sound]
source: https://strudel.cc/learn/synths/
status: verified
---

Sets the oscillator frequency directly in hertz.

## Parameters
- `hertz` (number | Pattern) — frequency in Hz.

## Returns
Pattern — the pattern playing at the given frequency.

## Examples
```js
// signature from official docs (synths page lists no explicit example for freq)
freq("220 330 440").s("sawtooth")
// plays a sawtooth at the given frequencies
```

## Gotchas
- `freq` takes raw hertz; `note` takes note names/semitones. Use whichever is more convenient — they target the same oscillator pitch.

## See also
- `note` — set pitch with note names instead of hertz.
