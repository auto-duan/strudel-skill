---
name: reset
category: transform
signature: "reset(pattern: string | Pattern): Pattern"
aliases: []
tags: [sync, restart, cycle, conditional]
related: [restart, mask, struct, when]
source: https://strudel.cc/learn/conditional-modifiers/
status: verified
---

Resets the source pattern to the start of the current cycle on each onset of the given pattern.

## Parameters
- `pattern` (string | Pattern) — the triggering pattern whose onsets cause a reset.

## Returns
Pattern — the source pattern, restarted at the current cycle boundary on each trigger.

## Examples
```js
s("[<bd lt> sd]*2, hh*8").reset("<x@3 x(5,8)>")
// the drum pattern resets to its beginning each time the reset pattern fires
```

## Gotchas
- `reset` only resets within the current cycle; it does not jump back to cycle 0.
- `restart` is the stronger variant that resets back to cycle 0 (the very beginning).
- Useful for creating polyrhythmic groove patterns that periodically sync.

## See also
- `restart` — like reset but jumps back to cycle 0 on each trigger.
- `mask` — silences events rather than restarting the pattern.
- `struct` — replaces the pattern's structure with a binary template.
