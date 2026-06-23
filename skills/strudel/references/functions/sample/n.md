---
name: n
category: sample
signature: "n(index: number | Pattern): Pattern"
aliases: []
tags: [sample, index, variant, select]
related: [s, bank, samples]
source: https://strudel.cc/learn/samples/
status: verified
---

Selects which variant (numbered from 0) within a sample bank to play.

## Parameters
- `index` (number | Pattern) — zero-based sample index. Values higher than the number of available variants wrap around (modulo).

## Returns
Pattern — the same pattern with the sample index set per event.

## Examples
```js
// Play the first four TR-909 hi-hat variants in sequence
s("hh*8").bank("RolandTR909").n("0 1 2 3")
// Indices 4-7 wrap: same sounds as 0-3 since TR909 hh only has 4
```

```js
// Equivalent colon-notation inside mini-notation
s("hh:0 hh:1 hh:2 hh:3").bank("RolandTR909")
```

## Gotchas
- Index is **zero-based**: the first sample is `n(0)`.
- Out-of-range indices wrap rather than throw an error.
- Inside mini-notation the `:N` colon shorthand is equivalent: `s("hh:2")` = `s("hh").n(2)`.
- `n` also doubles as a note/pitch selector in tonal contexts — meaning depends on whether `s` or `note` is the active audio source.

## See also
- `s` — the sample bank selector; `n` refines which variant within that bank.
- `bank` — prepend a drum-machine prefix; combine with `n` to browse individual hits.
