# 🥧 love-pi - π as a power ballad

A Monte Carlo estimation of **π**, written in the [Rockstar](https://codewithrockstar.com/)
programming language - and then turned into an actual song.

🎵 **Listen to it:** [pi on Suno](https://suno.com/song/614c53c6-83f0-4d41-8087-f8eedc26ccfe?sh=HQ6IOMLd3cPc1lrR)

---

## What is this?

This is a small experiment that sits at the intersection of three things:

1. **Rockstar** - an esoteric programming language whose defining feature is that
   valid programs also read like 1980s rock power-ballad lyrics. Variables are named
   things like `your love`, `the heavens`, `her eyes`; numbers are written as poems
   (the *length of each word* becomes a digit). Real code, real lyrics.

2. **The Monte Carlo method** - a way to approximate π using randomness instead of
   geometry.

3. **[Suno](https://suno.com/)** - an AI music generator. The idea was: if the source
   code already *reads* like song lyrics, why not feed it to Suno and let it sing the
   algorithm out loud?

So: this repository contains a working π estimator that is *also* a love poem that is
*also* a generated song.

## The algorithm - Monte Carlo π

The math is delightfully simple:

- Imagine a 1×1 square with a quarter-circle of radius 1 inscribed in it.
- The square has area `1`; the quarter-circle has area `π/4`.
- Throw a large number of random points into the square.
- The fraction of points that land *inside* the quarter circle (i.e. where
  `x² + y² < 1`) approaches `π/4`.
- Multiply that fraction by `4`, and you get an approximation of **π**.

The more darts you throw, the closer you get. No trigonometry required - just a lot of
random points and a counter.

## Reading the Rockstar

In [`love-pi.rock`](./love-pi.rock), the algorithm hides inside the romance:

- **Poetic number literals** - a line like `Your love is O we you love flame`
  isn't a sentence, it's the number `12345` (word lengths: `O`=1, `we`=2, `you`=3,
  `love`=4, `flame`=5).
- **Variables** - `the heavens`, `her eyes`, `his arms`, `the distance`, `the fate`
  are just storage for coordinates, accumulators, and the running estimate.
- **The loop** - `While the moment is less than my longing` is the sampling loop:
  it keeps throwing darts until it has thrown enough of them.
- **The hit test** - comparing `the distance` against `a heartbeat` (1) decides
  whether a point fell inside the circle.
- **The reveal** - `Whisper our love` is Rockstar's way of printing the final result:
  the approximation of π.

It computes π. It also breaks your heart a little.

## Running it

The quickest way is the official playground - paste
[`love-pi.rock`](./love-pi.rock) into <https://codewithrockstar.com/online> and run it.

This repo also includes a small Node setup (`rockstar-pi/`) that runs the program
through [`rockstar-strudel`](https://www.npmjs.com/package/rockstar-strudel), a
WASM-based Rockstar engine - fittingly, one that can also emit its output as musical
notes:

```js
const { init, rockstar_pro } = await import('https://esm.sh/rockstar-strudel')
await init()

const src = await fetch('./love-pi.rock').then(r => r.text())
const prog = await rockstar_pro([src])
console.log(prog.text_output) // the π approximation
```

```bash
cd rockstar-pi
npm install
```

(There are several Rockstar implementations - see the
[Rockstar site](https://codewithrockstar.com/) for the full list.)

## Why?

Because it was funny, mostly. Code that doubles as poetry that triples as music felt
like too good a coincidence to leave alone.

And if you follow the idea to its absurd conclusion: a Rockstar program is valid song
lyrics, a song can be published on Spotify, and a published song can be downloaded and
run. So in principle you could turn Spotify into a software distribution platform -
ship your programs as singles and let people stream your source code. :D
