---
name: loop
category: sound
signature: "loop(enabled: number | Pattern): Pattern"
aliases: []
tags: [sound, sample, playback, loop]
related: [loopBegin, loopEnd, begin, end]
source: https://strudel.cc/learn/samples/
status: verified
---

Loops the sample. Note that the tempo of the loop is not synced with the cycle tempo.

## Parameters
- `enabled` (number | Pattern) — `1` to loop, `0` to play once.

## Returns
Pattern — the pattern with sample looping enabled/disabled.

## Examples
```js
// from official docs
s("casio").loop(1)
// continuously loops the "casio" sample
```

## Gotchas
- Loop tempo is NOT synced to the cycle — the sample loops at its own length. Use `fit`, `loopAt`, or `chop` for cycle-synced playback.
- Combine with `loopBegin` / `loopEnd` to loop only a portion of the sample.

## See also
- `loopBegin` / `loopEnd` — define the looping region.
- `fit` — make a sample fit its event duration (cycle-synced).
