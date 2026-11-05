# 3D Woofer Radio

A compact, battery-powered internet radio with a **three-way front**: a woofer in the centre, a mid-range speaker either side and a tweeter at each end. It is inspired by the look and layout of the 1980s "3D Super Woofer" boomboxes, but it is **not a clone**: our own size, our own parts, no tape decks or CD.

> **Status: design stage.** Nothing has been built, printed or tested yet. The numbers below are first-pass estimates from published speaker data and need a bench test. Next: the 3D model.

Site: https://dylan7474.github.io/3d-woofer-radio/

## The idea

- A wide, low, rectangular cabinet with a **black metal speaker grille** across the front, each speaker sitting in its own **pod** (a recessed section of the grille, with its own sealed chamber behind).
- The pods sit **close together** across the front, as on the original, not spread out.
- **Centre:** a 5-inch woofer in its own sealed pod.
- **Either side of it:** a mid-range speaker in its own small sealed pod.
- **At each end:** a tweeter that marks the end of the cabinet, one on each side.
- A built-in rechargeable battery, so it can be carried from room to room.
- A "luxury" build: we use parts a mass producer would probably skip.

## Parts under consideration

| Job | Part | Notes |
|---|---|---|
| Mid-range (x2) | Visaton FR 10, 4 ohm, 4" full-range | Fs 90 Hz, Qts 0.54, Vas 2.3 L, 86 dB, 105 mm square frame. Reaches about 20 kHz. |
| Woofer | Dayton Audio DC130B-4, 5.25", 4 ohm | Fs about 51 Hz, Qts 0.35, Vas about 12 L ([Parts Express](https://www.parts-express.com/Dayton-Audio-DC130B-4-5-1-4-Classic-Woofer-Speaker-295-307)). Alternative: Visaton W130S-4 ([Loudspeaker Database](https://loudspeakerdatabase.com/VISATON/W130S-4)). |
| Tweeters (x2) | Dayton Audio AMT Mini-8, 8 ohm | About 40 mm round, 23 mm deep, 88 dB, 15 W ([Dayton](https://daytonaudio.com/product/1169/amt-mini-8-air-motion-transformer-tweeter-8-ohm)). Sits behind a tall, narrow **slot in the grille** for the vertical look of the original. Crossover point still to confirm. |
| Amplifier | 2.1 channel TPA3116 module, 2 x 50 W + 100 W | Has volume, treble, a bass crossover and a sub channel. 12-24 V. Two candidates: the AIYIMA board (about 14.49 pounds, sub cut-off 26-160 Hz) or the [Audiophonics](https://www.audiophonics.fr/en/amplifier-boards/module-amplificateur-tpa3116-p-22035.html) board (34.90 euros, crossover 0-200 Hz). See the bench test section. |
| Brain | Raspberry Pi (Zero 2 W for low power) | Plays the radio. |
| DAC | I2S DAC board (for example PCM5102 type) | The TPA3116 module takes an analog input, so the Pi needs a DAC in between. |
| Battery | Protected lithium-ion pack, about 12 V | Needs a proper charge/protection board and a fuse. Quality parts only: a bad battery build is a fire risk. |

## Speaker pods (first-pass sums)

Each speaker gets its own sealed chamber.

- **Mid pods:** with the woofer taking over at about 130-150 Hz, a sealed pod of **about 2-3 L** per FR 10 is enough (roughly 118-133 Hz roll-off). This is smaller than the 5.9 L ported pod used for a single full-range speaker.
- **Woofer pod (decided): 3 L sealed.** For the DC130B-4 that gives a smooth response (Qtc about 0.79) with the -3 dB point near 104 Hz. A bigger pod barely moves that point (4 L: 103 Hz, 6 L: 105 Hz), and 2.2 L saves only about 5 cm of depth at the cost of a small bump near 130 Hz. About 16-20 cm deep, in line with the mid pods, so the whole cabinet can be roughly 20 cm deep. A ported pod would reach about 58 Hz but needs about 9 L (over 50 cm deep at this width), so it is ruled out for a compact radio.
- **Size:** two mids, a woofer and two tweeter pods side by side come to roughly 480 mm wide and at least 155 mm high (first-pass, from the real frame sizes).

These come from the standard sealed-box formula and the published speaker parameters. Real enclosures, 3D-printed walls and the actual drivers will differ, so the plan is to build and measure.

## Bench test (before any cabinet is built)

Prices were checked on 5 November 2026 and will change. **Nothing has been ordered.**

| Item | Choice | Price seen | Notes |
|---|---|---|---|
| 2.1 amp | **AIYIMA TPA3116 2.1, "Without Bluetooth" option** ([AliExpress](https://www.aliexpress.com/item/1005005876605506.html)) | 14.49 pounds (sale to 18 Nov) | Sub cut-off 26-160 Hz, 12-25 V (3-4 A at 12 V), left/right 4-8 ohm, sub 2-8 ohm, 101 x 100 x 25 mm, five knobs. Seller 97.8% positive, about 89,700 followers. The Bluetooth versions cost 16.29 pounds (Bluetooth) and 16.89 pounds (Bluetooth + USB-stick input) and have the same five knobs in the photos. Free returns for 90 days. |
| Amp, alternative | Audiophonics 2.1 TPA3116 | 34.90 euros incl. VAT | Crossover 0-200 Hz confirmed on the page; shipped from France, so import charges may apply. |
| I2S DAC | GY-PCM5102 board (PCM5102A) | about 1.78-1.94 pounds on AliExpress | 5,000+ sold, 4.9 stars. Some boards need a solder bridge on the back to work with a Pi. |
| Supply | 12 V, 3 A or more, 5.5/2.1 mm | about 7.60-8.60 pounds (UK, generic) | Buy a mains supply from a UK seller, not AliExpress. |
| Supply, nicer | Variable bench supply, 30 V 5 A | about 32-44 pounds (UK) | Lets us test 9-12.6 V (the range of a 3-cell battery) and read idle current. |
| Source | Raspberry Pi 3 and a spare microSD card | already owned | Test on a standard Pi OS card first. |
| Odds and ends | 3.5 mm lead, inline fuse (about 3 A), speaker wire, jumper leads, film capacitors 2.2 / 3.3 / 4.7 uF (50 V or more) | a few pounds | For the tweeter high-pass and safety. |
| Speakers for the test | One Visaton FR 10 (as a mid) and any spare 4 ohm speaker (stands in for the woofer) | owned | Buy the DC130B-4 and the AMT Mini-8 only once the amp passes. |

Cheapest route is roughly 25 pounds (amp, DAC, fixed supply); about 50 pounds with the variable bench supply.

**Notes on the AIYIMA board:** the "USB" input only plays from a USB stick and cannot connect to a computer, so it is not a DAC; we still need the PCM5102 board. The description lists the five pots (bass volume, bass frequency, left/right volume, treble, total volume) under the Bluetooth version; the photo of the non-Bluetooth option shows the same five knobs, but that is not explicitly confirmed. One buyer reported a slight hum, possibly from a plug with no earth.

**What the test should answer**

1. Hiss and pops: is the idle noise acceptable, and does it click on power-up?
2. Crossover: does the bass knob hand over cleanly between the woofer and the FR 10 at about 130-150 Hz?
3. Tweeter load: does the amp stay happy with the Mini-8 and its filter in parallel with a mid?
4. Low voltage: does it still work at 9-12.6 V (a 3-cell battery)?
5. Idle current: how much does it draw doing nothing (for battery life)?

## Things to check

- Not every "2.1 TPA3116" board has a working crossover. Only buy one whose listing names the low-pass/crossover control.
- The sub output is rated 100 W into 2 ohm; a 4 ohm woofer gets less. At 12 V the output is lower again, which is still plenty for a 5-inch woofer in a small box.
- The 8 ohm Mini-8 wired in parallel with a 4 ohm mid could present as low as about 2.7 ohm where both play, below the amp's 4 ohm rating. A series capacitor keeps the tweeter quiet at low frequencies and the mid's impedance rises at the top, so the real load should stay higher, but this must be measured before trusting it.
- Dayton gives no recommended crossover for the Mini-8 (usable range from about 3.5-4 kHz up). Builders cross it around 5-6 kHz, and one suggests using it as a blended super-tweeter above about 10 kHz with a gentle slope. Plan: a first-order high-pass of roughly 6 kHz (a capacitor of about 3.3 uF), then adjust by ear and measurement.
- Battery safety, heat (the amp needs ventilation) and the weight of the cabinet.

## Next steps

1. **3D model of the cabinet and pods** (next): a rectangular cabinet about 480 mm wide, at least 155 mm high and about 20 cm deep, with five tightly packed pods behind a black metal grille (vertical slots for the tweeters), checked against the real parts before any printing.
2. Bench test the amp (see above) before committing to the cabinet.
3. Design the Mini-8 high-pass filter (start near 6 kHz, about 3.3 uF) and tune it by ear and measurement.
4. Choose the battery pack and charging board.

**Where we parked it (5 November 2026):** layout, speakers, pod sizes, tweeter and amp candidates are chosen; the bench test parts are listed but not bought; the 3D model has not been started.

## Credits

The look comes from the classic Hitachi 3D Super Woofer boomboxes of the 1980s. This project is not affiliated with Hitachi.
