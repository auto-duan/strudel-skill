---
title: Chord Progression with Auto Voicing
tags: [harmony, chords, voicing, tonal]
description: Plays a chord progression with automatic smooth voice leading via chord() and voicing().
source: https://strudel.cc/understand/voicings/
---
# Chord Progression with Auto Voicing

Type chord symbols, get musical harmony. `chord()` sets the symbols and
`voicing()` picks octave arrangements that move smoothly from one chord to the
next (voice leading), so you never have to spell out individual notes.

## Pattern
```js
chord("<Am C D F Am E Am E>").voicing().room(.5)
```

Arpeggiating individual voicing notes with `n()`:
```js
n("0 3 1 2").chord("<C <Fm Db>>").voicing().clip("4 3 2 1").room(.5)
```

## What it demonstrates
- `chord("<...>")` declares one chord per cycle using ireal-style symbols (`Am`, `G7`, `Bb^7`).
- `voicing()` realizes those symbols as notes with automatic smooth voice leading.
- `n("0 3 1 2")` indexes into the current voicing to arpeggiate it instead of strumming the block.
- `.room(.5)` adds reverb; `.clip()` controls note length for the arpeggio.
- Nested `<Fm Db>` shows sub-cycle chord changes inside a single slot.
