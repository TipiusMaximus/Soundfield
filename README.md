# Soundfield# Codex prompt: Pressure Field Lab v0.1

Build a single-file browser app called `Pressure Field Lab v0.1`.

## Goal

Create an interactive 2D pressure-field visualizer for PA/subwoofer layout experiments.

This is not meant to be a professional acoustic simulator. It is a fast visual thinking tool for comparing 2.0, 2.1, 4.0 and 6.0 speaker layouts.

## Hard requirements

- Create one file: `index.html`
- Use vanilla HTML, CSS and JavaScript only
- Use Canvas 2D
- No npm
- No build step
- No external libraries
- Must run by opening `index.html` directly in a browser

## Core features

1. Draw a top-down 2D dancefloor.
2. Show draggable sound sources.
3. Layout selector:
   - 2.0: left top+sub and right top+sub
   - 2.1: left/right tops and draggable center sub
   - 4.0: four totem points
   - 6.0: six surrounding points
4. Frequency slider: 35–120 Hz.
5. Heatmap showing summed pressure magnitude.
6. Each source has:
   - enabled checkbox
   - gain dB slider
   - delay ms slider
   - polarity toggle
7. Reset layout button.
8. Show coordinates and basic info.

## Simulation model

Use a simplified point-source model.

Constants:

```js
const SPEED_OF_SOUND = 343;
```

For each grid pixel/sample point:

```text
distance = distance from source to point in meters
phase = 2 * PI * frequency * distance / SPEED_OF_SOUND
phase += 2 * PI * frequency * delaySeconds
amplitude = gainLinear / Math.max(distance, 0.5)
pressure += polarity * amplitude * Math.cos(phase)
```

Display `Math.abs(pressure)` as heatmap intensity.

## Coordinate system

Use canvas pixels but map to meters.

Example:

```text
canvas width = 900 px
canvas height = 600 px
world width = 30 m
world height = 20 m
```

## Layout defaults

2.0:

```text
L top/sub: x=8, y=3
R top/sub: x=22, y=3
```

2.1:

```text
L top: x=8, y=3
R top: x=22, y=3
center sub: x=15, y=4
```

4.0:

```text
front left: x=6, y=4
front right: x=24, y=4
rear left: x=6, y=16
rear right: x=24, y=16
```

6.0:

```text
six points around the dancefloor oval/circle
```

## UI notes

Make it beginner-friendly:

- clear labels
- short helper text
- no jargon-only controls
- responsive enough for laptop screen

## Stretch goals if easy

- Add `Animate` button for slow modulation.
- Add preset: `breathing field` where gains slowly move between sources.
- Add preset: `rotating field` for 4.0.
- Add preset: `drop lock` where sources align toward dancefloor center.
- Add JSON export/import of source positions and settings.

## Acceptance test

After implementation:

1. Open `index.html` in browser.
2. Select 2.0 and 80 Hz.
3. Select 2.1 and 80 Hz.
4. Drag the center sub and confirm the heatmap updates.
5. Change delay/gain/polarity and confirm heatmap updates.
6. Select 4.0 and 6.0 and confirm sources appear correctly.

## Tone of project

The research idea is:

> Embrace the Phase. Compose the Pressure Field.

Keep the code simple and readable so the next iteration can add real measurements later.
