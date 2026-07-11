# Pressure Field Lab v0.3.1

A lightweight browser-based field lab for low-frequency speaker layout and crossover exploration. This version adds a more balanced 2.0 vs 2.1 comparison, a simplified complex crossover response, per-source phase offset, and source-specific modulation targets.

## What it calculates
- pressure field magnitude from point sources
- complex summation of real and imaginary pressure components
- source gain, delay, polarity, type, enabled state, and phase offset
- simplified complex crossover response for Top and Sub sources using Linkwitz–Riley 12/24 dB/oct responses
- single-frequency and broadband RMS field values
- compare maps for 2.0 and 2.1 layouts with per-cabinet or total-source-power normalization
- listener distance, delay, phase, and relative amplitude

## What it does not calculate
- speaker directivity or real radiation patterns
- cabinet size or physical enclosure effects
- line-array geometry
- room reflections or floor reflections
- air absorption
- actual speaker phase response
- amplifier or limiter behavior

## Running the app
Open `index.html` directly in a modern browser, or run a simple server from the repository root:

```bash
python3 -m http.server 8000
```

Then open `http://127.0.0.1:8000`.

## Controls
- `Analysis mode`: choose `Single frequency` or `Broadband`
- `Display mode`: choose `Single layout`, `Compare 2.0 vs 2.1`, or `Difference`
- `Frequency`: 35–200 Hz (single frequency mode)
- `Crossover frequency`: 60–140 Hz
- `Filter slope`: 12 dB/oct or 24 dB/oct
- `Crossover response`: Linkwitz–Riley 12/24 dB/oct
- Source cards: enable/disable, gain, delay, phase offset, polarity, and source type
- Listener: drag the green listener point on the canvas
- Animation: turn on slow modulation, rotate, focus, or drop lock behavior
- Modulation: toggle modulation per source, select gain/delay/phase targets, and tune modulation depth

## Layouts
- `2.0`: left/right top and left/right sub at the same x/y positions for balanced comparison
- `2.1`: left/right top plus two center sub positions at the same x/y position for balanced comparison
- `4.0`: four full-range positions
- `6.0`: six full-range totem positions

## Using 2.0 vs 2.1 comparison
- Select `Compare 2.0 vs 2.1` to view both maps side by side.
- Select `Difference` to see red when 2.0 is stronger and blue when 2.1 is stronger.
- Both comparison modes use the same frequency, crossover, modulation, and visual scale.

## Trying 4.0 and 6.0
- Switch layout to `4.0` or `6.0` in `Single layout` mode.
- Use the listener point and source controls to explore field behavior.

## Notes
- Top-down sources that share the same x/y location are treated as time-aligned by default, so delay and phase offset are separate controls.
- Delay affects the result as a frequency-dependent propagation delay. Phase offset adds a fixed phase angle at the selected frequency and is simplified for broadband use.
- The crossover is a simplified electrical crossover model, not a full loudspeaker model.
- Below 160 Hz the model is useful for basic pressure and phase interference.
- Between 160–200 Hz the model is a transition approximation for sub/top integration.
- Above 200 Hz the point-source approximation is not reliable and results should be interpreted with caution.

## Next step
The next small improvement would be to replace the point-source model with measured speaker responses or real acoustic impulse data.
