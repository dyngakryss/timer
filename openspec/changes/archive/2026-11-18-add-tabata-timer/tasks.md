# Tasks

## 1. Tabata Settings

- [x] 1.1 Add Tabata-specific settings for work duration, rest duration, round count, and startup countdown with the specified defaults; verify the fields appear only in Tabata mode and valid values apply to the next session.
- [x] 1.2 Validate Tabata duration, round-count, and startup-countdown inputs; verify malformed or non-positive durations, non-positive or fractional rounds, and invalid countdown values are rejected without changing accepted settings.

## 2. Tabata Timing Lifecycle

- [x] 2.1 Implement Tabata startup countdown and work/rest phase transitions using deadline-based timing; verify zero countdown starts Work immediately, positive countdown precedes Work, and each Work phase transitions to Rest at full duration.
- [x] 2.2 Implement round advancement and completion after the final rest period; verify round progress advances only after rest, including the final rest, then the timer completes at zero.
- [x] 2.3 Implement Tabata phase rendering, accessible phase/round status, pause/resume, Stop during startup countdown, and Reset behavior; verify each control preserves or clears phase progress as specified.

## 3. Timer Mode Navigation

- [x] 3.1 Add Tabata to the ordered three-mode carousel and active-mode guard; verify swipe and keyboard navigation order, non-wrapping endpoints, and that running work/rest or startup countdown prevents mode changes.

## 4. Integration Verification

- [x] 4.1 Browser-test Tabata settings, countdown, work/rest transitions, round completion, stop/reset/pause/resume, and accessibility; verify existing Stopwatch and Intervals behavior and navigation still work.
