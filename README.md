# TapVid FM

> Music for thinking & building — an audio-reactive particle field in the TapVid brand language.

A single self-contained web page: play calm public-domain piano/cello, and a flowing
noise particle field (Tappy Green → Signal Purple) moves to the music — its swirl speed,
color and ripple are driven by the audio's **frequency spectrum and waveform**.

**Live:** https://bobobobo-creator.github.io/tapvid-fm/

## Use

- Click anywhere or press `Space` to play / pause.
- `◀ / ▶` buttons or `←` / `→` to switch tracks.
- Volume slider · `⛶` fullscreen.
- `F` cycles the particle field density / trail presets — **flow · calm · storm**.

## How it works

- Plain HTML + Canvas2D + the Web Audio API. No build step, no dependencies (just web fonts).
- `<audio>` → Web Audio analyser; the particle flow field reads `getByteFrequencyData`
  (spectrum) and `getByteTimeDomainData` (waveform) each frame.
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

## Code license

MIT — see `LICENSE`. (Applies to the code only; audio keeps the licenses above.)
