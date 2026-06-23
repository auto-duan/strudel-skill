---
name: s
category: sample
signature: "s(name: string | Pattern): Pattern"
aliases: [sound]
tags: [sample, playback, drum, sound]
related: [n, bank, samples, soundAlias, speed, begin, end]
source: https://strudel.cc/learn/samples/
status: verified
---

Selects and plays a named sample (or synth) from the loaded sample map.

## Parameters
- `name` (string | Pattern) — the sample bank name, optionally suffixed with `:N` to pick a specific variant (e.g. `"hh:2"`). Mini-notation patterns are accepted.

## Returns
Pattern — a pattern of audio events that trigger the named sample on each active step.

## Examples
```js
// Basic drum beat using default built-in samples
s("bd sd [~ bd] sd, hh*16, misc")
// bd=bass drum, sd=snare, hh=hi-hat, misc=miscellaneous; comma separates simultaneous layers
```

```js
// Select specific sample variant with colon notation
s("bd*4, hh:0 hh:1 hh:2 hh:3 hh:4 hh:5 hh:6 hh:7")
  .bank("RolandTR909")
// colon index wraps around if higher than available variants
```

## Gotchas
- `s` and `sound` are aliases; they behave identically.
- The first variant of each sample is index `0`, not `1`.
- Indices that exceed the number of available variants wrap around (modulo).
- Samples are lazy-loaded: the very first trigger of a sample may be silent while the file loads.
- `s` selects a sample bank; `n` selects the variant index within that bank. Using `:N` inside `s` is shorthand for chaining `.n(N)`.

## See also
- `n` — select sample variant by index (alternative to the `:N` colon shorthand).
- `bank` — prepend a drum-machine prefix to all sample names in a pattern.
- `samples` — load a custom sample map so new names become available to `s`.
- `soundAlias` — create a short alias for an existing sample name.
- `speed` — change playback speed / pitch of the triggered sample.
