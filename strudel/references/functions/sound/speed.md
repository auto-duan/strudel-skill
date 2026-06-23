---
name: speed
category: sound
signature: "speed(speed: number | Pattern): Pattern"
aliases: []
tags: [sound, sample, pitch, playback]
related: [begin, end, loop, note, n]
source: https://strudel.cc/learn/samples/
status: verified
---

Alters sample playback velocity — an economical way to change pitch (and duration) of a sample.

## Parameters
- `speed` (number | Pattern) — playback rate. `1` = normal, `2` = double speed/up an octave, negative values play the sample backwards.

## Returns
Pattern — the pattern with altered playback speed.

## Examples
```js
// from official docs
s("bd*6").speed("1 2 4 1 -2 -4")
// speeds up, slows, and reverses the kick
speed("1 1.5*2 [2 1.1]").s("piano").clip(1)
// pitches a piano sample by changing its playback rate
```

## Gotchas
- Changing speed also changes pitch (it does not time-stretch); negative values reverse playback.
- Affects sample playback specifically; for synth oscillators use `note`/`freq`.

## See also
- `begin` / `end` — trim the played region of the sample.
- `note` — set pitch for synths and pitched samples.
