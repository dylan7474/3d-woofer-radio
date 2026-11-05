# 3D Woofer Radio

A compact, battery-powered internet radio with a **three-way front**: a woofer in the centre, a mid-range speaker either side and a tweeter at each end. It is inspired by the look and layout of the 1980s "3D Super Woofer" boomboxes, but it is **not a clone**: our own size, our own parts, no tape decks or CD.

> **Status: idea stage.** Nothing has been built, printed or tested yet. The numbers below are first-pass estimates from published speaker data and need a bench test.

Site: https://dylan7474.github.io/3d-woofer-radio/

## The idea

- A wide, low, rectangular cabinet with three speaker panels across the front.
- **Centre:** a 5-inch woofer in its own sealed pod.
- **Either side of it:** a mid-range speaker in its own small sealed pod.
- **At each end:** a small tweeter.
- A built-in rechargeable battery, so it can be carried from room to room.
- A "luxury" build: we use parts a mass producer would probably skip.

## Parts under consideration

| Job | Part | Notes |
|---|---|---|
| Mid-range (x2) | Visaton FR 10, 4 ohm, 4" full-range | Fs 90 Hz, Qts 0.54, Vas 2.3 L, 86 dB, 105 mm square frame. Reaches about 20 kHz. |
| Woofer | Dayton Audio DC130B-4, 5.25", 4 ohm | Fs about 51 Hz, Qts 0.35, Vas about 12 L ([Parts Express](https://www.parts-express.com/Dayton-Audio-DC130B-4-5-1-4-Classic-Woofer-Speaker-295-307)). Alternative: Visaton W130S-4 ([Loudspeaker Database](https://loudspeakerdatabase.com/VISATON/W130S-4)). |
| Tweeters (x2) | Small 8 ohm tweeters with a series capacitor | Not chosen yet. Ideally **vertical** (tall and narrow) like the original boombox: desirable, not essential. The FR 10 already reaches high frequencies, so the tweeters add sparkle rather than range. |
| Amplifier | 2.1 channel TPA3116 module, 2 x 50 W + 100 W | Has volume, treble, a bass crossover (0-200 Hz) and a sub channel for 3-4 ohm loads. 12-24 V. About 35 euros from [Audiophonics](https://www.audiophonics.fr/en/amplifier-boards/module-amplificateur-tpa3116-p-22035.html). |
| Brain | Raspberry Pi (Zero 2 W for low power) | Plays the radio. |
| DAC | I2S DAC board (for example PCM5102 type) | The TPA3116 module takes an analog input, so the Pi needs a DAC in between. |
| Battery | Protected lithium-ion pack, about 12 V | Needs a proper charge/protection board and a fuse. Quality parts only: a bad battery build is a fire risk. |

## Speaker pods (first-pass sums)

Each speaker gets its own sealed chamber.

- **Mid pods:** with the woofer taking over at about 130-150 Hz, a sealed pod of **about 2-3 L** per FR 10 is enough (roughly 118-133 Hz roll-off). This is smaller than the 5.9 L ported pod used for a single full-range speaker.
- **Woofer pod:** for the DC130B-4, about **4 L** sealed (roll-off near 100 Hz) or about **2.2 L** (near 130 Hz).
- **Width:** two mids, a woofer and two tweeters side by side come to roughly 500-550 mm.

These come from the standard sealed-box formula and the published speaker parameters. Real enclosures, 3D-printed walls and the actual drivers will differ, so the plan is to build and measure.

## Things to check

- Not every "2.1 TPA3116" board has a working crossover. Only buy one whose listing names the low-pass/crossover control.
- The sub output is rated 100 W into 2 ohm; a 4 ohm woofer gets less. At 12 V the output is lower again, which is still plenty for a 5-inch woofer in a small box.
- A 4 ohm tweeter in parallel with a 4 ohm mid would present about 2 ohm, so use 8 ohm tweeters.
- Battery safety, heat (the amp needs ventilation) and the weight of the cabinet.

## Next steps

1. Pick the tweeters.
2. Check the amp with a bench test before building the cabinet.
3. Design the cabinet and pods, and check every part against the real hardware before printing.

## Credits

The look comes from the classic Hitachi 3D Super Woofer boomboxes of the 1980s. This project is not affiliated with Hitachi.
