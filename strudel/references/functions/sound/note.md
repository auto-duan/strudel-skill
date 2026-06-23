---
name: note
category: sound
signature: "note(pitch: string | number | Pattern): Pattern"
aliases: []
tags: [sound, pitch, tonal, synth]
related: [freq, n, sound, speed]
source: https://strudel.cc/learn/synths/
status: verified
---

Sets the pitch using note names (with octaves) or MIDI-style numbers.

## Parameters
- `pitch` (string | number | Pattern) — note names like `c2`, `eb3`, `g4`, or numeric values. Patterns of notes are supported.

## Returns
Pattern — the pattern playing at the given pitch(es).

## Examples
```js
// from official docs
note("c2 <eb2 <g2 g1>>".fast(2))
// plays a moving bassline; defaults to a triangle oscillator
```

## Gotchas
- If you set `note` without an explicit `sound`, the default oscillator is `triangle`.
- Use `freq` to specify a pitch directly in hertz instead of note names.

## See also
- `freq` — set pitch directly in hertz.
- `n` — index into sample banks or apply a semitone offset depending on context.
