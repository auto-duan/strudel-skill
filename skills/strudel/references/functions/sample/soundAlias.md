---
name: soundAlias
category: sample
signature: "soundAlias(originalName: string, alias: string): void"
aliases: []
tags: [sample, alias, rename, shortcut]
related: [s, samples, bank]
source: https://strudel.cc/learn/samples/
status: verified
---

Creates a short alias for an existing sample name so it can be referenced by the new name in `s`.

## Parameters
- `originalName` (string) — the full existing sample name (e.g. `'RolandTR808_bd'`).
- `alias` (string) — the new short name to create (e.g. `'kick'`).

## Returns
void — registers the alias as a side effect; no pattern returned.

## Examples
```js
// Create an alias and use it immediately
soundAlias('RolandTR808_bd', 'kick')
s("kick")
```

## Gotchas
- Like `samples`, `soundAlias` is a **setup call** — it must run before the pattern that uses the alias.
- The original name must already be in the sample map; `soundAlias` does not load new audio files.
- Aliases do not support variant arrays — they map a single name to a single existing entry.

## See also
- `samples` — load new sample maps and define names from scratch.
- `s` — uses any registered name (built-in, loaded via `samples`, or aliased via `soundAlias`).
- `bank` — a pattern-level prefix strategy as an alternative way to shorten long drum-machine names.
