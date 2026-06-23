---
name: release
category: sound
signature: "release(time: number | Pattern): Pattern"
aliases: [rel]
tags: [sound, envelope, adsr, amplitude]
related: [attack, decay, sustain, adsr]
source: https://strudel.cc/learn/effects/
status: verified
---

Amplitude envelope release time: how long the sound takes to fade from the sustain level to zero after the note ends.

## Parameters
- `time` (number | Pattern) — release time in seconds.

## Returns
Pattern — the pattern with the release stage set.

## Examples
```js
// from official docs
note("c3 e3 g3 c4").release("<0 .1 .4 .6 1>/2")
// progressively longer fade-outs / tails
```

## Gotchas
- The release happens after the note's "off" point, so it can extend the sound past its step duration (events may overlap).
- Part of the ADSR amplitude envelope.

## See also
- `sustain` — the level the release fades down from.
- `adsr` — set attack, decay, sustain, release together.
