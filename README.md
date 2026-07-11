# Pressure Field Lab v0.2

A lightweight browser-based field lab for low-frequency speaker layout and crossover exploration. This version adds broadband analysis, source types, a simplified crossover model, listener measurement, animation modes, and 2.0 vs 2.1 comparison.

## What it calculates
- pressure field magnitude from point sources
- complex summation of real and imaginary pressure components
- source gain, delay, polarity, type, and enabled state
- simplified crossover rolloff for Top and Sub sources
- single-frequency and broadband RMS field values
- compare maps for 2.0 and 2.1 layouts
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
- Source cards: enable/disable, gain, delay, polarity, and source type
- Listener: drag the green listener point on the canvas
- Animation: turn on slow modulation, rotate, focus, or drop lock behavior

## Layouts
- `2.0`: left/right top and left/right sub
- `2.1`: left/right top plus center sub
- `4.0`: four full-range positions
- `6.0`: six full-range totem positions

## Using 2.0 vs 2.1 comparison
- Select `Compare 2.0 vs 2.1` to view both maps side by side.
- Select `Difference` to see red when 2.0 is stronger and blue when 2.1 is stronger.
- Both comparison modes use the same frequency, crossover, and visual scale.

## Trying 4.0 and 6.0
- Switch layout to `4.0` or `6.0` in `Single layout` mode.
- Use the listener point and source controls to explore field behavior.

## Notes
- Below 160 Hz the model is useful for basic pressure and phase interference.
- Between 160–200 Hz the model is a transition approximation for sub/top integration.
- Above 200 Hz the point-source approximation is not reliable and results should be interpreted with caution.

## Next step
The next small improvement would be to replace the point-source model with measured speaker responses or real acoustic impulse data.
