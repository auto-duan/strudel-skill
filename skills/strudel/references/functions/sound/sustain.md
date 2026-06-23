---
name: sustain
category: sound
signature: "sustain(level: number | Pattern): Pattern"
aliases: [sus]
tags: [sound, envelope, adsr, amplitude]
related: [attack, decay, release, adsr]
source: https://strudel.cc/learn/effects/
status: verified
---

Amplitude envelope sustain level: the level held after the attack and decay stages, until the note is released.

## Parameters
- `level` (number | Pattern) — sustain level, `0` to `1`.

## Returns
Pattern — the pattern with the sustain level set.

## Examples
```js
// from official docs
note("c3 e3 f3 g3").decay(.2).sustain("<0 .1 .4 .6 1>")
// from fully plucky (0) to a fully held tone (1)
```

## Gotchas
- `sustain` is a *level* (0–1), not a time — unlike attack/decay/release which are durations.
- `sustain(0)` makes the sound die after the decay, regardless of note length.

## See also
- `decay` — the time to fall to this sustain level.
- `release` — the fade-out time after the note ends.
