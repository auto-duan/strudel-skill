---
name: bank
category: sample
signature: "bank(name: string | Pattern): Pattern"
aliases: []
tags: [sample, drum-machine, bank, prefix]
related: [s, n, samples]
source: https://strudel.cc/learn/samples/
status: verified
---

Prepends a drum-machine (or other bank) name to every sample name in the pattern, so short standard names like `bd` and `hh` resolve to the full prefixed names like `RolandTR808_bd`.

## Parameters
- `name` (string | Pattern) — the bank prefix. Will be joined to each sample name with `_`.

## Returns
Pattern — same structure, with every sample name prefixed.

## Examples
```js
// Play TR-808 drums using short names
s("bd sd, hh*16").bank("RolandTR808")
// equivalent to: s("RolandTR808_bd RolandTR808_sd, RolandTR808_hh*16")
```

```js
// Pattern the bank itself to alternate between drum machines each cycle
s("bd sd, hh*16").bank("<RolandTR808 RolandTR909>")
```

## Gotchas
- `bank` only works because the abbreviated names (`bd`, `sd`, etc.) are standardised across the `tidal-drum-machines` library. Custom sample packs don't follow this convention automatically.
- Some banks are missing samples for certain standard abbreviations — if a sound is silent, check whether that bank includes it.
- `bank` is syntactic sugar: it does nothing more than prepend `<bankName>_` to the sample string; the full name must exist in the loaded sample map.

## See also
- `s` — the sample player that uses the fully resolved name after `bank` prepends its prefix.
- `n` — choose the variant index within the resolved bank entry.
- `samples` — register custom sample maps so bank-prefixed names are available.
