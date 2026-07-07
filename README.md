# sines-tarn

16 FM sine waves for norns — a stripped-down, frequency-first fork of
[sines](https://github.com/groundforms/sines) by @oootini.

Each voice is an FM sine (configurable carrier/modulator FM index) with its own
per-voice sample rate, bit depth, amplitude envelope, pan, and a per-voice
chorus. Pitch is set directly in Hz rather than as scale notes.

## What's different from `sines`

* pitch is edited as **frequency in Hz**, not scale notes / MIDI note numbers
* added a per-voice **chorus** (amount on E3, rate in the params menu)
* removed all **crow** output functions
* removed the **envelope-follower** play mode
* removed **z_tuning** support (the note/scale tuning model no longer applies)
* removed the **scale** and **root note** params (voices are tuned directly in Hz)
* added a global **chorus rate** param, overridable per voice in each voice group

The engine SuperCollider class is `Engine_SinesTarn`, so this coexists with the
original `sines` script without conflict.

## Installation

Ensure norns is up to date. In the maiden console, run:

```
;install https://github.com/groundforms/sines-tarn
```

Then `SYSTEM => RESET` on norns to pick up the SuperCollider engine, and restart
for good measure.

Installing this way clones the repo with git, so maiden's project manager will
show an **update** action from then on — pull new commits straight from norns.

## Defaults

On a fresh install the 16 voices boot to solfeggio-family frequencies ascending
147 → 963 Hz, panned left / middle / right in sets of three, with all effects at
zero and sample rate at 48k. Everything is tuned in Hz and adjustable per voice.
There's a global `chorus rate` in the top-level params; each voice's rate can be
overridden in its own `n voice` group.

## Controls

**sines page**
* `E1` — select active sine (1–16)
* `E2` — frequency, ± 10 Hz
* `E3` — frequency, ± 0.5 Hz
* `K2` — toggle sines / ctrl page

**ctrl page** (`K2`)
* `E1` — select param line (1–4)
* line 1 — `E2` freq ±10 Hz / `E3` freq ±0.5 Hz
* line 2 — `E2` envelope / `E3` env delay
* line 3 — `E2` sample bitrate / `E3` FM index
* line 4 — `E2` pan / `E3` **chorus**

**16n**
* `n` — sine volume

## MIDI control

The 16n fader controller is mapped by default; other MIDI controllers work too.
Per-voice amplitude, envelope, bit depth, sample rate, FM index and chorus are
all exposed in the norns parameters menu for mapping.

## Credits

Forked from `sines` by @oootini, with contributions from @p3r7, @sixolet,
@tomwaters, @JosueArias, @x2mirko. Engine derived from @catfact's zebra.
