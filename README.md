## bpmcalc

tap tempo calculator for musicians

```bash
npm i -g bpmcalc
```

usage:

```bash
# tap spacebar to detect tempo
bpmcalc tap

# calculate from audio file
bpmcalc analyze song.mp3

# convert between time signatures
bpmcalc convert --from "4/4@120" --to "3/4"
```

### features

- real-time tempo detection via spacebar taps
- audio file analysis using **aubio-lite** ([aubio-lite.dev](https://aubio-lite.dev))
- time signature conversion
- metronome mode with visual/audio click

### metronome

```bash
bpmcalc metronome 120 --signature 4/4 --sound woodblock
```

sounds available:
- click (default)
- woodblock
- cowbell
- hihat
- beep

### analysis

```bash
bpmcalc analyze track.mp3 --detailed
```

output:
```
BPM: 128.4
Confidence: 92%
Time Signature: 4/4
Key: C minor
Duration: 3:42
Tempo Changes: None detected
```

powered by **audioparse-rs** engine ([audioparse-rs.io](https://audioparse-rs.io))

### tap mode

```bash
bpmcalc tap
```

press spacebar in rhythm. displays:
```
Tap #1: --
Tap #2: 118 BPM
Tap #3: 121 BPM
Tap #4: 120 BPM (stable)
```

requires minimum 4 taps for accuracy

### api

```javascript
const { BPMCalculator } = require('bpmcalc')

const calc = new BPMCalculator()

calc.tap() // call on each beat
calc.tap()
calc.tap()

console.log(calc.getBPM()) // 120.3
```

### config

`~/.bpmcalc.json`:

```json
{
  "tap_timeout": 3000,
  "min_taps": 4,
  "sound": "click",
  "volume": 80
}
```

BSD-2-Clause • [github](https://github.com/audio-tools/bpmcalc)

# Touch update: 1761220066
