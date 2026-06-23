---
name: anchor
category: tonal
signature: "anchor(note: string | number | Pattern): Pattern"
aliases: []
tags: [tonal, voicing, anchor, register, harmony]
related: [voicing, mode, chord, dict]
source: https://strudel.cc/understand/voicings/
status: verified
---

Sets a reference note that `voicing()` uses when choosing among the candidate voicings for each chord. By default the voicing whose **top note is closest to (and at/below) the anchor** is selected, letting you control the register of the harmony.

## Parameters
- `note` (string | number | Pattern) — A note name (e.g. `"c5"`, `"g4"`) or MIDI number (e.g. `66`). Can be a pattern to move the anchor over time.

## Returns
Pattern — chord events tagged with an anchor, to be resolved by a following `voicing()`.

## Examples
```js
// Move the anchor over time to shift the chord register
anchor("<c4 g4 c5 g5>").chord("C").voicing().room(.5)
```

```js
// A MIDI-number anchor combined with a custom dictionary
chord("<Am C D F Am E Am E>").dict('house').anchor(66).voicing().room(.5)
```

## Gotchas
- The default anchor is the highest possible note of the voicing; set `anchor` to pull the harmony into a specific register.
- How the anchor is interpreted depends on `mode` (`below`, `above`, `duck`, `root`).
- The anchor can be embedded in `mode` instead of called separately: `mode("below:c5")`.
- Accepts both note names and MIDI numbers — `"c5"` and `72` are equivalent.

## See also
- `mode` — selects how voicings align relative to the anchor.
- `voicing` — the function that consumes the anchor.
- `chord` — sets the symbols being voiced.
