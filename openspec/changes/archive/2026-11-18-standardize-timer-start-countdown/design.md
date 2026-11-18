# Design

## Context

The standalone page implements stopwatch, interval, and Tabata timing in `index.html`. Each mode currently owns its startup-countdown state and exposes a separate countdown setting; interval and Tabata also use Settings for duration and round configuration. See proposal.md for motivation and specs/ for the behavior contract.

## Goals / Non-Goals

**Goals:**
- Keep the three modes' current pause, cancellation, reset, and timer progression behavior.
- Make countdown and cue timing independent of delayed display refresh callbacks.
- Keep the page dependency-free and usable as a standalone HTML file.

**Non-Goals:**
- Add sound, countdown, or other settings.
- Add cues at interval round or Tabata work/rest transitions.
- Persist settings or timer state across page reloads.

## Decisions

- Replace the three configurable startup durations with one shared fixed value of 10 seconds. Keep each mode's existing countdown phase and deadline handling so the fixed countdown remains separate from stopwatch elapsed time and from interval/Tabata work durations. A cancelled attempt starts a fresh countdown; resuming a paused timer phase does not.
- Generate the cues with the browser Web Audio API. The session-start cue SHALL last 0.9 seconds (twice its previous 0.45-second duration), use a slightly lower pitch, and be slightly louder than the short countdown cues. Initialize or resume audio in response to the Start button gesture so playback follows browser autoplay restrictions; do not add an audio library or sound asset.
- Trigger the short cue once as the displayed startup countdown reaches each of 3, 2, and 1 seconds, and trigger the longer, lower-pitched cue once at the transition into stopwatch timing, interval round 1, or Tabata work round 1. Track cue progress for the active attempt so the periodic render loop cannot replay a cue. Reset that progress on cancellation or a fresh attempt. Resuming a paused timer does not replay startup cues.
- Remove the countdown inputs and their validation/state from Settings. Retain the interval and Tabata settings needed for their work durations and round counts. Remove the stopwatch Settings control because its countdown input is its only remaining setting.

## Risks / Trade-offs

- Browser audio may be unavailable or muted → create/resume the audio context from the user-initiated Start action and avoid making timer progression depend on audio playback.
- Delayed or throttled callbacks can skip a displayed second → continue deriving countdown display from its deadline and guard cues against repeats; emit a cue only when the corresponding remaining second is observed.
- A user who relied on configurable countdown duration will now receive 10 seconds → this is the requested behavior; no migration action is needed.

## Migration Plan

No persisted data or external APIs are involved. Remove countdown settings and use the fixed startup behavior in all modes. Rolling back restores the current configurable settings and timer behavior.
