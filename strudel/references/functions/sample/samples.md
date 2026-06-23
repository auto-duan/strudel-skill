---
name: samples
category: sample
signature: "samples(map: object | string, basePath?: string): void"
aliases: []
tags: [sample, loader, custom, bank, setup]
related: [s, n, bank, soundAlias]
source: https://strudel.cc/learn/samples/
status: verified
---

Loads a custom sample map, making new sample names available to `s`. Accepts an inline object, a URL to a `strudel.json` file, or GitHub/Shabda shortcut strings.

## Parameters
- `map` (object | string) — one of:
  - An object mapping name → file path (string) or array of paths.
  - A URL string pointing to a `strudel.json` file.
  - A GitHub shortcut string `"github:<user>/<repo>/<branch>"` (branch defaults to `main`).
  - A Shabda shortcut string `"shabda:<sound>:<count>,..."` to pull samples from freesound.org.
- `basePath` (string, optional) — base URL prepended to each relative sample path when `map` is an inline object.

## Returns
void — registers the sample names as a side effect; no pattern returned.

## Examples
```js
// Inline map with a base URL
samples({
  bassdrum: 'bd/BT0AADA.wav',
  hihat: 'hh27/000_hh27closedhh.wav',
  snaredrum: ['sd/rytm-01-classic.wav', 'sd/rytm-00-hard.wav'],
}, 'https://raw.githubusercontent.com/tidalcycles/Dirt-Samples/master/')

s("bassdrum snaredrum:0 bassdrum snaredrum:1, hihat*16")
```

```js
// Load from a strudel.json URL
samples('https://raw.githubusercontent.com/tidalcycles/Dirt-Samples/master/strudel.json')
s("bd sd bd sd, hh*16")
```

```js
// GitHub shortcut (looks for strudel.json at repo root on main branch)
samples('github:tidalcycles/dirt-samples')
s("bd sd bd sd, hh*16")
```

```js
// Shabda: pull samples from freesound.org by keyword
samples('shabda:bass:4,hihat:4,rimshot:2')
$: n("0 1 2 3 0 1 2 3").s('bass')
$: n("0 1*2 2 3*2").s('hihat').clip(1)
$: n("~ 0 ~ 1 ~ 0 0 1").s('rimshot')
```

```js
// Pitched sample map: key = note name, value = file
samples({
  'moog': { 'g3': 'moog/005_Mighty%20Moog%20G3.wav' },
}, 'github:tidalcycles/dirt-samples')
note("g3 bb3 c4").s('moog').clip(1)
```

## Gotchas
- `samples` is a **setup call**, not a pattern function — it must be called before the pattern runs, usually at the top of the REPL editor.
- Browsers aggressively cache `strudel.json`; append a query param (e.g. `?v=2`) to bust the cache during development.
- When `map` is an inline object, each value is joined with `basePath` to form the final URL — make sure both parts together form a valid URL.
- A pitched map (`{ note: file }`) makes the sampler automatically pitch-shift to the nearest declared root note. This notation is also valid inside `strudel.json`.
- Overriding a built-in name (e.g. `bd`) is possible and will replace the default.

## See also
- `s` — plays samples by name once they are registered via `samples`.
- `n` — selects the variant index within a bank.
- `bank` — prepend a drum-machine prefix; does not require `samples`.
- `soundAlias` — create a short alias for an already-loaded sample name.
