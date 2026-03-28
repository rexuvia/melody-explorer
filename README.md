# 🎵 Melody Explorer

A browser-based microtonal melody generator and rating tool. Explore the full spectrum of random sound, rate what you hear, and export your findings as JSON.

**Live Demo:** [rexuvia.com/games/melody-explorer.html](https://rexuvia.com/games/melody-explorer.html)

---

## What It Does

Melody Explorer uses the **Web Audio API** to synthesize short 6-note melodic sequences from randomly generated frequencies. After each melody plays, you rate it on a scale of 0–10. All your ratings are logged in a table and can be exported as a structured JSON file.

It's part music toy, part data-collection experiment — what makes a random sequence feel "good"? You decide.

---

## Features

- 🎲 **Random 6-note melodies** — frequencies drawn logarithmically from 100 Hz to 8000 Hz for perceptually rich variety
- 🎵 **Smooth audio playback** — sine/triangle oscillators with attack/release envelopes (no clicks or pops)
- ⏱ **Variable timing** — 100–400 ms random delay between each note
- 📊 **Live note visualiser** — animated waveform bars during playback
- 💊 **Note pills** — each frequency shown as a highlighted pill during playback
- ⭐ **0–10 rating slider** — rate the melody after it plays
- 🔁 **Replay button** — re-listen before rating or from the history table
- 📋 **Saved history table** — all rated melodies displayed with frequencies, delays, and rating
- ⬇ **Export JSON** — download all saved melodies as a structured `.json` file

---

## How to Use

1. **Click "▶ Play New Melody"** — a 6-note sequence plays automatically.
2. **Watch the note pills** — each frequency lights up as it plays.
3. **Rate the melody** — drag the slider to a value from 0 (awful) to 10 (perfect).
4. **Click "💾 Save Rating"** — the entry is added to the table below.
5. **Repeat** as many times as you like.
6. **Click "⬇ Export JSON"** to download all your data.

You can also **replay** any saved melody by clicking the ▶ button in the history table row.

---

## Exported JSON Format

```json
[
  {
    "id": 1,
    "rating": 7,
    "freqs": [432, 1091, 247, 3800, 612, 1540],
    "delays": [210, 380, 150, 300, 120, 400],
    "timestamp": "2026-03-28T23:00:00.000Z"
  }
]
```

| Field       | Type     | Description                                     |
|-------------|----------|-------------------------------------------------|
| `id`        | number   | Sequential entry ID                             |
| `rating`    | number   | User rating (0–10)                              |
| `freqs`     | number[] | Array of 6 frequencies in Hz                   |
| `delays`    | number[] | Array of 6 inter-note delays in milliseconds    |
| `timestamp` | string   | ISO 8601 datetime when the rating was saved     |

---

## Technical Details

- **Single-file app:** Pure HTML/CSS/JavaScript — no build step, no dependencies.
- **Audio engine:** Web Audio API (`AudioContext`, `OscillatorNode`, `GainNode`)
- **Waveforms:** Randomly chosen sine or triangle per note
- **Frequency distribution:** Log₂-uniform over [100, 8000] Hz — biased toward the perceptually rich midrange
- **Envelope:** 20 ms attack, 35 ms sustain plateau, 60 ms release — eliminates click artifacts
- **Styling:** Dark neon/synthwave aesthetic — mobile-first, CSS custom properties

---

## Browser Compatibility

Works in any modern browser that supports the Web Audio API:
- Chrome / Edge 66+
- Firefox 76+
- Safari 14.1+
- Mobile Chrome / Safari (iOS 14.5+)

> **Note:** The first click is required to unlock the AudioContext on iOS/Safari due to browser autoplay policies.

---

## License

MIT — free to use, fork, and remix.

---

*Part of the [Rexuvia](https://rexuvia.com) experimental web apps collection.*
