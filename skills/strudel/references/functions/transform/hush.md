---
name: hush
category: transform
signature: "hush(): Pattern"
aliases: []
tags: [silence, mute, utility]
related: [mask, never, degrade]
source: https://strudel.cc/learn/conditional-modifiers/
status: verified
---

Silences a pattern unconditionally, producing no events.

## Parameters
None.

## Returns
Pattern — an empty (silent) pattern.

## Examples
```js
stack(s("bd").hush(), s("hh*3"))
// the kick is silenced; only the hi-hat plays
```

## Gotchas
- `hush` completely removes all events from the pattern — it is not probabilistic.
- Useful for quickly muting one voice inside a `stack` without removing the line.
- For probabilistic or conditional silencing use `mask`, `degrade`, or `never`.

## See also
- `mask` — silences events where a binary mask is 0/`~`.
- `never` — applies a function with 0% probability (effectively a no-op rather than silence).
- `degrade` — randomly removes 50% of events.
