# TapVid FM

> Music for thinking & building — an audio-reactive particle field in the TapVid brand language.

A single self-contained web page: play calm public-domain piano/cello, and a dense
WebGL2 flow field (Tappy Green → Signal Purple) moves to the music — a grid of points
domain-warped by fractal 4D simplex noise, with its displacement, swirl speed, color and
ripple driven by the audio's **frequency spectrum and waveform**.

**Live:** https://bobobobo-creator.github.io/tapvid-fm/

## Use

- Click anywhere or press `Space` to play / pause.
- `◀ / ▶` buttons or `←` / `→` to switch tracks.
- Volume slider · `⛶` fullscreen.
- `F` cycles the particle field density / trail presets — **flow · calm · storm**.

## How it works

- Plain HTML + WebGL2 + the Web Audio API. No build step, no dependencies (just web fonts).
- A grid of ~70k–270k points (density preset dependent) is displaced in a vertex shader by
  fractal 4D simplex noise; feedback trails fade each frame.
- `<audio>` → Web Audio analyser; the spectrum (`getByteFrequencyData`) and waveform
  (`getByteTimeDomainData`) are uploaded as textures and sampled per column in the shader.
- Over `http(s)` the field reacts to the real audio. Opened as a local `file://` the
  browser silences the Web Audio graph (null-origin media), so the page plays the audio
  directly and animates from a synthetic envelope instead. **Hosting it (this Pages link)
  is what makes the real audio-reactivity work.**
- If no audio file loads, it falls back to a small procedurally-generated lofi loop so it's
  never silent.

## Add / change tracks

Drop CC0 / public-domain MP3s into `audio/` and edit the `PLAYLIST` array near the top of
the `<script>` in `index.html`.

## Audio credits & licenses

| Track | Source | License |
| --- | --- | --- |
| Chopin — Nocturne Op.9 No.2 | [Musopen – Complete Chopin Collection](https://archive.org/details/musopen-chopin) | **CC0 1.0** (public domain) |
| Chopin — Prélude Op.28 No.15 "Raindrop" | [Musopen – Complete Chopin Collection](https://archive.org/details/musopen-chopin) | **CC0 1.0** (public domain) |
| J.S. Bach — Cello Suite No.1, Prélude (BWV 1007) | Performed by **Matthieu Fontana** · [archive.org](https://archive.org/details/Bach_Suite1ForVioloncelloSolo_MatthieuFontana) | **CC BY-NC-ND 3.0** |

The Bach cello recording is shared unmodified, for non-commercial use, with attribution
to the performer, per CC BY-NC-ND 3.0.

## Visual credits

The flow-field technique is ported from **"Not Safe" by ZRNOF**
([openprocessing.org/sketch/2956548](https://openprocessing.org/sketch/2956548)), a recode in
the #RecodeRethink curation, inspired by [Etienne Jacob](https://bleuje.com/). The GLSL noise
is reused under its MIT licenses (headers kept in the shader source):

- 4D simplex noise — Ian McEwan / Ashima Arts / [stegu](https://github.com/stegu/webgl-noise) (MIT)
- `snoise4DImage` + `displace` — © 2023 Zaron (MIT)

## Code license

MIT — see `LICENSE`. (Applies to the new code only; the GLSL noise keeps its MIT headers,
and the audio keeps the licenses above.)
