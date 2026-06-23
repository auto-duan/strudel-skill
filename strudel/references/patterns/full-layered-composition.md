---
title: Full Layered Composition
tags: [composition, stack, drums, bassline, chords, synthesis]
description: A complete track stacking drums, a generative bassline, and voiced chords with synthesis.
source: https://strudel.cc/learn/getting-started/
---
# Full Layered Composition

The capstone example from the official getting-started page. It `stack()`s three
independent layers — drums, a bassline with pitch/timbre movement, and a voiced
chord pad — into one evolving piece, showing how Strudel's pieces compose.

## Pattern
```js
samples({
  bd: ['bd/BT0AADA.wav','bd/BT0AAD0.wav','bd/BT0A0DA.wav','bd/BT0A0D3.wav','bd/BT0A0D0.wav','bd/BT0A0A7.wav'],
  sd: ['sd/rytm-01-classic.wav','sd/rytm-00-hard.wav'],
  hh: ['hh27/000_hh27closedhh.wav','hh/000_hh3closedhh.wav'],
}, 'github:tidalcycles/dirt-samples');
stack(
  s("bd,[~ <sd!3 sd(3,4,2)>],hh*8")
    .speed(perlin.range(.7,.9))
  ,"<a1 b1*2 a1(3,8) e2>"
    .off(1/8, x=>x.add(12).degradeBy(.5))
    .add(perlin.range(0,.5))
    .superimpose(add(.05))
    .note()
    .decay(.15).sustain(0)
    .s('sawtooth')
    .gain(.4)
    .cutoff(sine.slow(7).range(300,5000))
  ,"<Am7!3 <Em7 E7b13 Em7 Ebm7b5>>".voicings('lefthand')
    .superimpose(x=>x.add(.04))
    .add(perlin.range(0,.5))
    .note()
    .s('sawtooth')
    .gain(.16)
    .cutoff(500)
    .attack(1)
)
.slow(3/2)
```

## What it demonstrates
- `samples({...}, 'github:...')` loads a custom sample bank with multiple variants per name.
- `stack(...)` plays drums, bass, and chords simultaneously as independent layers.
- Generative motion: `perlin`/`sine` LFOs drive `speed`, pitch `add`, and `cutoff` over time.
- `off`, `superimpose`, and `degradeBy` create echoes, detuned doublings, and probabilistic thinning.
- `voicings('lefthand')` realizes the chord line from a named voicing dictionary.
- `note()` converts the bass/chord values to pitch; `.s('sawtooth')` synthesizes them.
- `.slow(3/2)` stretches the whole stack to set the overall tempo.
