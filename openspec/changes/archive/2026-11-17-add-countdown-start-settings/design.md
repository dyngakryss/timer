# Design

## Context

The stopwatch is a self-contained HTML page with inline CSS and JavaScript. Its current timer tracks elapsed duration and a start timestamp; see proposal.md for motivation and specs/stopwatch/spec.md for the behavior contract.

## Goals / Non-Goals

**Goals:**
- Keep the feature dependency-free and directly usable from the standalone page.
- Keep countdown timing accurate when browser callbacks are delayed.
- Make countdown and stopwatch states mutually exclusive so cancellation and resuming are predictable.

**Non-Goals:**
- Persist settings across page reloads or add countdown sounds, notifications, or repeating timers.

## Decisions

- Add a Settings button and an in-page panel with a numeric input and explicit apply action. Validate that the value is a non-negative integer before accepting it; use zero as the initial value and keep the accepted value in memory for the page session. This avoids introducing storage or ambiguity about when edits take effect.
- Represent a pending countdown separately from stopwatch elapsed time. Start from zero establishes a countdown deadline; display remaining whole seconds using the existing minutes-and-seconds format. When the deadline is reached, clear countdown state and start the elapsed timer at zero. A zero setting bypasses countdown and starts immediately.
- Calculate countdown remaining time from its deadline instead of decrementing a counter on each interval. This prevents callback delays from extending the countdown.
- Stop during countdown cancels the attempt and returns to idle at 00:00; another Start begins a fresh countdown. Reset also cancels countdown and clears elapsed time while preserving the configured setting. Pause/resume applies only after stopwatch timing begins and does not repeat the countdown.
- Keep the existing periodic display refresh and use one active refresh interval for either countdown or stopwatch operation. This minimizes timer lifecycle complexity and ensures reset/stop clear pending updates.

## Risks / Trade-offs

- A hidden or throttled tab may not visually update on every second → derive remaining countdown time from its deadline so it catches up on the next refresh.
- Editing invalid numeric input can vary across browsers → validate the parsed value explicitly before applying it and leave the accepted setting unchanged on failure.
- Settings are lost on page reload → this is intentional for the requested session-only behavior and avoids adding persistence.

## Migration Plan

No migration is required. The existing page remains directly openable; removing the new controls and countdown state rolls back the feature.
