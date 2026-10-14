# Moondrop Chu III EQ

An EQ profile for the **Moondrop Chu III**, made with [AutoEq](https://github.com/jaakkopasanen/AutoEq). AutoEq doesn't have the Chu III in its database yet, so apps that use AutoEq's list (such as Wavelet) don't offer it.

![Moondrop Chu III frequency response and EQ](./Moondrop%20Chu%20III.png)

## Files

| File | Use it for |
|------|------------|
| `Moondrop Chu III GraphicEQ.txt` | Wavelet (Android), Equalizer APO / Peace (Windows), and other apps that import AutoEq GraphicEQ files |
| `Moondrop Chu III ParametricEQ.txt` | Parametric equalizers: apps that take filters with a frequency, gain and Q |
| `Moondrop Chu III FixedBandEQ.txt` | Ordinary 10-band equalizers (31 Hz to 16 kHz) |
| `Moondrop Chu III.png` | The graph above |

## How to use it

### Wavelet (Android)

1. Download `Moondrop Chu III GraphicEQ.txt` to your phone.
2. Import it in Wavelet. Wavelet can import AutoEq GraphicEQ files; where the option sits depends on your version.
3. Use one headphone profile at a time. If Wavelet's AutoEq is still set to another model (the Chu 2, say), turn it off or replace it, so the two corrections don't stack.
4. Keep Wavelet's limiter on.

### Parametric EQ

Set the preamp first so the boosts can't clip.

**Preamp: -5.2 dB**

| # | Type | Frequency | Gain | Q |
|---|------|-----------|------|---|
| 1 | Low shelf | 105 Hz | -0.6 dB | 0.70 |
| 2 | Peak | 170 Hz | -3.9 dB | 0.73 |
| 3 | Peak | 5468 Hz | +5.2 dB | 2.08 |
| 4 | Peak | 730 Hz | +2.1 dB | 1.28 |
| 5 | Peak | 2118 Hz | +0.7 dB | 3.16 |
| 6 | High shelf | 10000 Hz | -1.3 dB | 0.70 |
| 7 | Peak | 3222 Hz | -0.6 dB | 4.15 |
| 8 | Peak | 4271 Hz | +0.7 dB | 4.94 |
| 9 | Peak | 1274 Hz | -0.3 dB | 3.22 |
| 10 | Peak | 969 Hz | +0.3 dB | 4.08 |

If your app only has 5 filters, use 1 to 5. Filters 6 to 10 are small refinements.

### 10-band EQ

**Preamp: -3.1 dB**

| 31 Hz | 62 Hz | 125 Hz | 250 Hz | 500 Hz | 1 kHz | 2 kHz | 4 kHz | 8 kHz | 16 kHz |
|-------|-------|--------|--------|--------|-------|-------|-------|-------|--------|
| -1.0 | -0.5 | -3.2 | -2.9 | +0.9 | +1.3 | -0.4 | +2.9 | +2.0 | -3.3 |

## What it changes

- **Upper bass:** about -4 dB around 170 Hz. Less bloom, so the mids come through more clearly. The sub-bass is barely touched.
- **Lower mids:** about +2 dB around 730 Hz, for a little more body in vocals and instruments.
- **Treble:** about +5 dB around 5.5 kHz, filling a dip in the Chu III's response that can leave detail sounding a little held back.
- **Air:** about -1 dB above 10 kHz.

## How it was made

1. **Measurements.** Chu III measurements from three squig.link databases: [precog](https://precog.squig.link), [CSI-Zone](https://csi-zone.squig.link) and [Aftersound](https://aftersound.squig.link). Each one's left and right channels were averaged and set to 0 dB at 1 kHz, then the three were averaged together. They agree closely: within about 0.5 to 0.8 dB RMS of each other from 20 Hz to 8 kHz. A fourth measurement, from [Earphones Archive](https://earphonesarchive.squig.link), differed clearly from the other three and was left out.
2. **EQ.** Generated with AutoEq 4.1.2:
   ```
   python -m autoeq --input-file "Moondrop Chu III.csv" --output-dir results --target "AutoEq in-ear.csv" --bass-boost 8 --parametric-eq --fixed-band-eq --fs 48000
   ```
   The target is AutoEq's own in-ear target with an 8 dB bass shelf, the same settings AutoEq uses for its published in-ear results.
3. **Check.** The same steps run on [Kazi's](https://kazi.squig.link) Moondrop Chu 2 measurement reproduce AutoEq's published result for that measurement to within 0.01 dB.

The averaged measurement isn't included here, since the data belongs to the people who measured it. It's freely viewable on their sites.

## Limits

- **It's a starting point, not a perfect fit.** Measurement rigs model an average ear. Above about 5 kHz, your own ear canal, the tips you use and how deep they sit can change what you hear by several dB.
- **If it sounds sharp or tiring,** lower the band around 5 to 6 kHz first. That boost is the least certain part of the profile.
- **Want more bass?** Raise the bass below about 100 Hz to taste.
- **Units vary.** Your pair can differ from the measured ones by a dB or two.

## Credits

- Measurements: **precog**, **CSI-Zone** and **Aftersound**, for publishing their measurements.
- [AutoEq](https://github.com/jaakkopasanen/AutoEq) by Jaakko Pasanen, which did the EQ maths.

Not affiliated with Moondrop.
