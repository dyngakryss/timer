# Proposal

## Why

Startup countdowns can currently be configured separately for the stopwatch, interval timer, and Tabata timer, so users must manage redundant settings and may get inconsistent starts. A fixed 10-second countdown with consistent audible cues gives every mode the same predictable preparation period.

## What Changes

- **BREAKING** Remove the configurable startup-countdown settings from the stopwatch, interval, and Tabata Settings panels.
- Apply a fixed 10-second startup countdown whenever any of the three modes starts a new session.
- Play a short beep as the countdown displays 3, 2, and 1, followed by a 0.9-second beep that is slightly louder and lower-pitched when the stopwatch or timer session begins.
- Preserve existing pause, resume, stop, and reset behavior around the startup countdown.

## Capabilities

### New Capabilities

### Modified Capabilities
- `stopwatch`: Replace the configurable startup countdown with a fixed countdown and add start cues.
- `interval-timer`: Replace the configurable startup countdown with a fixed countdown and add start cues.
- `tabata-timer`: Replace the configurable startup countdown with a fixed countdown and add start cues.

## Impact

- Updates the standalone `index.html` settings UI, timer state, and audio behavior.
- No external dependencies or API changes.
