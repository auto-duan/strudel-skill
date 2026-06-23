---
name: arrange
category: structure
signature: "arrange(...sections: [number, Pattern][]): Pattern"
aliases: []
tags: [combination, arrangement, multi-cycle, structure]
related: [cat, seq, stack, stepcat]
source: https://strudel.cc/learn/factories/
status: verified
---

Arranges multiple patterns together over multiple cycles by specifying explicit cycle counts for each section.

## Parameters
- `...sections` ([number, Pattern][]) — variable number of `[cycles, pattern]` pairs; each pair plays its pattern for the given number of cycles before moving to the next.

## Returns
Pattern — a long-form pattern that cycles through each section for its allotted cycle count.

## Examples
```js
arrange(
  [4, "<c a f e>(3,8)"],
  [2, "<g a>(5,8)"]
).note()
// plays the first pattern for 4 cycles, then the second for 2 cycles, then repeats (6-cycle loop)
```

## Gotchas
- Unlike `cat` (where each item is always exactly 1 cycle), `arrange` lets you give each section any number of cycles.
- The total loop length is the sum of all cycle counts in the argument list.
- Each section pattern is played at its natural speed within its allotted cycles — a pattern with mini-notation `<a b c>` inside a 4-cycle section will cycle through a, b, c, a over those 4 cycles.

## See also
- `cat` — concatenates patterns, each for exactly **one** cycle.
- `seq` / `fastcat` — concatenates patterns, all within **one** cycle equally.
- `stepcat` — concatenates proportional to step count within one cycle.
