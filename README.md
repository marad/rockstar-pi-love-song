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

## Why?

Because it was funny, mostly. Code that doubles as poetry that triples as music felt
like too good a coincidence to leave alone.

And if you follow the idea to its absurd conclusion: a Rockstar program is valid song
lyrics, a song can be published on Spotify, and a published song can be downloaded and
run. So in principle you could turn Spotify into a software distribution platform -
ship your programs as singles and let people stream your source code. :D

## Running it

The quickest way is the official playground - paste
[`love-pi.rock`](./love-pi.rock) into <https://codewithrockstar.com/online> and run it.

This repo also ships a tiny browser demo in [`rockstar-pi/`](./rockstar-pi) that runs
the program live and shows the π it sings:

```bash
cd rockstar-pi
npm start          # serves the repo on http://localhost:3000
```

Then open <http://localhost:3000/rockstar-pi/>. It prints `3.14108` - a real Monte
Carlo estimate, computed by the ballad. Rockstar has no random-number primitive, so
the "randomness" is a deterministic pseudo-random recurrence built from arithmetic -
which means the estimate is reproducible: same lyrics, same π, every run.

Under the hood the demo uses [`rockstar-strudel`](https://www.npmjs.com/package/rockstar-strudel),
a WASM-based Rockstar engine - fittingly, one built for the [strudel.cc](https://strudel.cc/)
live-coding REPL, so it can also emit its output as musical notes. Note that it's a
*browser* engine (it loads .NET WASM from a CDN and needs `window`), so it doesn't run
under plain Node - hence the little static server above.

(There are several Rockstar implementations - see the
[Rockstar site](https://codewithrockstar.com/) for the full list.)
