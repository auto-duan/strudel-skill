---
title: Basic Drum Pattern
tags: [rhythm, drums, samples, beginner]
description: A minimal four-on-the-floor-style drum line built from sample names in mini-notation.
source: https://strudel.cc/learn/getting-started/
---
# Basic Drum Pattern

The simplest way to make a beat in Strudel: feed drum sample names to `s()` as a
mini-notation string. Each name triggers one sample, evenly spaced across the cycle.

## Pattern
```js
s("bd sd cp hh")
```

## What it demonstrates
- `s()` plays named samples (`bd` kick, `sd` snare, `cp` clap, `hh` hi-hat).
- A space-separated mini-notation string divides one cycle into equal steps.
- Order in the string = order in time; four tokens = four equal sixteenth-of-a-bar-style hits.
- Starting from `s("bd sd")` and adding tokens is the canonical "grow a beat" workflow.
