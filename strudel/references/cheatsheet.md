# Strudel Cheatsheet

High-density reference for writing Strudel (<https://strudel.cc/>) code. Verified
against this repo's function docs and official sources (fetched 2026-06-23).
Mini-notation lives inside `"..."` (double quotes) or `` `...` `` (backticks).
Single quotes `'...'` are NOT parsed. Chain transforms with `.method()`.
Run/update with Ctrl-Enter; stop with Ctrl-. (period).

## Mini-Notation Syntax

| Symbol | Meaning | Example |
|---|---|---|
| space | Separate events in one cycle; split time evenly | `"c e g"` |
| `~` / `-` | Rest / silence | `"c ~ e ~"` |
| `[ ]` | Sub-sequence in one slot (nested subdivision) | `"c [e g] c"` |
| `< >` | Per-cycle alternation (one event per cycle) | `"<c e g>"` |
| `*n` | Repeat/speed up within the slot | `"c*2"`, `"[c e]*2"` |
| `/n` | Slow: one event over n cycles | `"[c e g d]/2"` |
| `,` | Parallel / chord (simultaneous) | `"[c,e,g]"` |
| `@n` | Elongate: take n shares of time | `"c@3 e"` |
| `!n` | Replicate as equal-length events | `"c!3 e"` = `"c c c e"` |
| `?` / `?p` | Degrade: drop ~50% (or p) of events | `"c*8?"`, `"c*8?0.3"` |
| `\|` | Random choice per cycle | `"[c\|e\|g]"` |
| `(p,s,o?)` | Euclidean: pulses, steps, offset | `"bd(3,8)"`, `"bd(3,8,2)"` |
| `:n` | Sample index in a bank (0-based, wraps) | `"bd:3 hh:1"` |

Notes: `*` is repeat/fill, NOT pitch math. `@` changes time share; `!` adds
equal events. `<a b>` == `[a b]/2`. Comma `,` inside `[]` = chord.

## Core Pattern Creation

| Function | Purpose | Example |
|---|---|---|
| `s(name)` / `sound` | Play named sample/synth | `s("bd sd hh")` |
| `note(x)` | Absolute pitch (names or numbers) | `note("c e g")` |
| `n(x)` | Sample variant index, OR scale degree with `.scale()` | `n("0 2 4").scale("C:major")` |
| `stack(...)` / `pr` | Layer patterns SIMULTANEOUSLY | `stack(drums, bass)` |
| `cat(...)` / `slowcat` | Sequence: one FULL cycle each | `cat("c","e","g")` |
| `seq(...)` / `fastcat` | Sequence: all within ONE cycle | `seq("c","e","g")` |
| `arrange([n,pat],...)` | Song arrangement (n cycles each) | `arrange([2,a],[2,b])` |
| `stepcat` / `timecat` | Concatenate weighted by step counts | `stepcat([3,a],[1,b])` |

Mini-notation equivalents: `stack` == `"a,b"`; `seq` == `"a b"`; `cat` ==
`"<a b>"`. Prefer JS forms when mixing `.s()` and `.note()` parts.

## Key Transforms

| Function | Purpose | Example |
|---|---|---|
| `fast(n)` / `density` | Speed up whole pattern (n<1 slows) | `.fast(2)` |
| `slow(n)` / `sparsity` | Stretch whole pattern | `.slow(2)` |
| `rev()` | Reverse each cycle independently | `.rev()` |
| `jux(fn)` | Apply fn to right channel only (stereo) | `.jux(rev)` |
| `every(n, fn)` | Apply fn every n cycles | `.every(4, fast(2))` |
| `firstOf` / `lastOf(n,fn)` | fn on first / last of every n cycles | `.firstOf(4, rev)` |
| `when(test, fn)` | Apply fn when boolean pattern is true | `.when("<0 1>", fast(2))` |
| `euclid(p,s)` | Euclidean rhythm (pulses, steps) | `.euclid(3,8)` |
| `euclidRot(p,s,r)` | Euclidean with rotation offset | `.euclidRot(3,8,2)` |
| `euclidLegato(p,s)` | Euclidean, pulses sustain (no gaps) | `.euclidLegato(3,8)` |
| `ply(n)` | Repeat EACH event n times | `.ply(2)` |
| `off(t, fn)` | Layer a copy delayed by t, transformed | `.off(1/8, x=>x.add(7))` |
| `superimpose(fn)` | Layer transformed copy, no time offset | `.superimpose(x=>x.add(12))` |
| `layer(...fns)` | Stack multiple transformed copies | `.layer(x=>x, rev)` |
| `echo(n, t, fb)` | n echoes, t apart, feedback gain | `.echo(3, 1/8, 0.5)` |
| `chunk(n, fn)` | Apply fn to a rotating 1/n slice | `.chunk(4, fast(2))` |
| `iter(n)` | Shift start by 1/n each cycle | `.iter(4)` |
| `mask(pat)` / `struct(pat)` | Gate / impose boolean structure | `.struct("t f t t")` |
| `add` / `sub` / `mul` | Arithmetic on values (e.g. transpose) | `.add(note("0 7"))` |
| `range(lo, hi)` | Remap a signal's output range | `sine.range(0,7)` |
| `segment(n)` | Sample a continuous signal into n events | `sine.segment(8)` |
| `hush()` | Silence the pattern | `.hush()` |

## Key Effects / Control Params

| Param | Purpose | Range / note |
|---|---|---|
| `gain(x)` | Volume | 0..1+ (1 = unity) |
| `pan(x)` | Stereo position | 0 left .. 1 right (0.5 center) |
| `lpf(x)` / `cutoff` | Low-pass filter cutoff (Hz) | e.g. 200..8000 |
| `hpf(x)` / `hcutoff` | High-pass filter cutoff (Hz) | |
| `lpq(x)` / `resonance` | Filter resonance / Q | |
| `room(x)` | Reverb send amount | 0..1 |
| `size(x)` / `roomsize` | Reverb room size | |
| `delay(x)` | Delay send amount | 0..1 |
| `delaytime(x)` | Delay time | cycles/seconds |
| `delayfeedback(x)` | Delay feedback | 0..1 |
| `crush(x)` | Bitcrush (bit depth) | low = grittier |
| `shape(x)` | Waveshape distortion | 0..1 |
| `speed(x)` | Sample playback speed (and pitch) | neg = reverse |
| `begin/end(x)` | Sample start/end fraction | 0..1 |
| `coarse(x)` | Downsample / sample-rate reduction | |
| `vowel(x)` | Formant filter | `"a e i o u"` |

ADSR envelope (amplitude): `.attack(a).decay(d).sustain(s).release(r)`
(times in seconds, sustain is a level 0..1). Filter envelope:
`.lpattack/.lpdecay/.lpsustain/.lprelease` with `.lpenv(amount)`.

## Signals / LFO

Continuous signals output **0..1** by default; sample with `.segment(n)` or use
to modulate params. `name2` variants (e.g. `sine2`) output **-1..1**.

| Signal | Shape |
|---|---|
| `sine` / `cosine` | Smooth sinusoid (cosine = quarter-phase offset) |
| `saw` / `isaw` | Ramp up / down |
| `tri` | Triangle |
| `square` | Square / pulse |
| `rand` | Continuous random (white noise value) |
| `perlin` | Smooth (Perlin) noise |
| `irand(n)` | Random integer 0..n-1 |

Usage: `n(sine.segment(16).range(0,15)).scale("C:minor")`,
`s("hh*8").gain(rand.range(0.4,1))`, `.lpf(saw.range(200,2000).slow(4))`.

## Tonal (scale / chord / pitch)

| Function | Purpose | Example |
|---|---|---|
| `scale(name)` | Map `n` degrees → notes (0-based) | `n("0 2 4").scale("C:major")` |
| `chord(name)` | Build a chord | `chord("C Am F G")` |
| `transpose(n)` | Shift by semitones / interval | `.transpose(7)` or `.transpose("3M")` |
| `scaleTranspose(n)` | Shift by scale steps in active scale | `.scaleTranspose(3)` |
| `voicing()` | Realize chord voicings | `chord("<C^7 Am7>").voicing()` |

Scale format: `root:type`, root defaults to octave 3 (`"C:major"` → C3).
Multi-word names use colons: `"C:bebop:major"`. Degrees past scale length
auto-octave up; negatives wrap below. `scale` pairs with `n`, not `note`.
Changing scale per cycle: `.scale("C:<major minor>/2")`.

## Quick Recipes

```js
// Basic beat
s("bd sd [~ bd] sd, hh*8")

// Drum machine bank + variants
s("bd*4, hh:0 hh:1 hh:2 hh:3").bank("RolandTR909")

// Bassline in a scale, filtered, with movement
n("0 3 5 7").scale("C:minor").s("sawtooth")
  .lpf(sine.range(300,1500).slow(4)).room(.3)

// Euclidean stereo melody
note("c3 eb3 g3").euclid(5,8).jux(rev).off(1/8, x=>x.add(12))

// Layered arrangement
stack(
  s("bd(3,8), hh*8"),
  note("c2 eb2 g2 bb2").s("sawtooth").lpf(800)
)
```
