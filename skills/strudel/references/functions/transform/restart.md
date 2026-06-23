---
name: restart
category: transform
signature: "restart(pattern: string | Pattern): Pattern"
aliases: []
tags: [sync, restart, cycle, conditional]
related: [reset, mask, struct, when]
source: https://strudel.cc/learn/conditional-modifiers/
status: verified
---

Restarts the source pattern from cycle 0 on each onset of the given pattern. Unlike `reset`, which only resets the current cycle, `restart` returns all the way to the very beginning.

## Parameters
- `pattern` (string | Pattern) — the triggering pattern whose onsets cause a full restart from cycle 0.

## Returns
Pattern — the source pattern, restarted from cycle 0 on each trigger.

## Examples
```js
s("[<bd lt> sd]*2, hh*8").restart("<x@3 x(5,8)>")
// the drum pattern jumps all the way back to cycle 0 each time the restart pattern fires
```

## Gotchas
- `restart` resets to cycle 0, making `<>` alternations and pattern history restart completely.
- `reset` only resets within the current cycle — a subtler effect.
- Both can create interesting polyrhythmic or phrase-repeat effects.

## See also
- `reset` — resets to the start of the current cycle, not cycle 0.
- `mask` — silences events conditionally.
- `struct` — imposes a new binary structure on the pattern.
