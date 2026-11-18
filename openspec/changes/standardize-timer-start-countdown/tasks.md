# Tasks

## 1. Remove configurable startup countdown settings

- [x] 1.1 Remove the stopwatch, interval, and Tabata countdown inputs, validation, and configuration state from `index.html`; remove the stopwatch-only Settings button while retaining interval duration/round and Tabata work/rest/round settings. Verify each Settings panel exposes only its remaining supported settings.

## 2. Apply the fixed startup countdown

- [x] 2.1 Update stopwatch starts from zero to use a deadline-based 10-second countdown, preserving cancellation, reset, and pause/resume behavior. Verify a fresh start counts down from 10, cancellation followed by Start begins at 10 again, and resuming elapsed timing does not repeat the countdown.
- [x] 2.2 Update interval and Tabata new sessions to use the same fixed 10-second countdown before round 1 or work round 1, preserving existing round durations and progress. Verify countdown cancellation/reset starts fresh and pausing/resuming an active round or phase does not repeat it.

## 3. Add audible startup cues

- [x] 3.1 Add dependency-free audio cues that play once at displayed countdown values 3, 2, and 1 and a 0.9-second, slightly louder and lower-pitched cue at the transition into stopwatch timing, interval round 1, or Tabata work round 1. Verify all modes emit the three short cues and one start cue without repeats, and that resuming a paused timer emits no startup cues.

## 4. Verify timer behavior

- [x] 4.1 Run the app and check all three modes end-to-end: 10-second startup, stop/reset during startup, pause/resume after timing begins, interval round advancement/completion, Tabata work/rest progression/completion, and retained duration/round settings. Verify the countdown settings are absent and startup cues match the specified timing, duration, and relative pitch/volume.
