# Design

## Context

The app is a standalone page with separate state for Stopwatch, Intervals, and Tabata. Shared start, stop, reset, and render functions dispatch to the selected mode. `timerIsRunning()` identifies active phases, including startup countdowns; rendering also advances deadline-based timers and detects completion.

## Goals / Non-Goals

**Goals:**
- Keep screen wake-lock state aligned with whether the selected timer is actively counting.
- Handle browser visibility changes without changing timer state or timing calculations.
- Keep timers usable when the browser lacks wake-lock support or a request is rejected.

**Non-Goals:**
- Keep the display awake while a timer is paused, stopped, or complete.
- Keep the timer page executing while hidden or guarantee a screen lock on browsers/devices that do not support or grant one.
- Add user settings or controls for wake-lock behavior.

## Decisions

- Use the browser Screen Wake Lock API when available. It is designed to prevent display sleep without entering fullscreen or adding a dependency.
- Centralize acquisition and release around the existing active-timer state rather than adding separate wake-lock state to each timer mode. Synchronize after start/stop/reset, after render updates that may complete a timer, and on document visibility changes.
- Keep at most one active wake-lock sentinel and guard asynchronous requests against races: if timing stops or the page becomes hidden before a request resolves, release the newly returned sentinel instead of retaining it.
- When a wake lock is released by the browser as the page is hidden, clear the stored sentinel. On return to visibility, request it again only if a timer is still active.
- Treat unsupported APIs and rejected requests as a wake-lock limitation, not a timer error. Leave the existing timer controls and deadline-based calculations unchanged.

## Risks / Trade-offs

- Wake-lock support and availability vary by browser, security context, operating system, and power state → continue normal timer operation when acquisition is unsupported or rejected; the app cannot promise to prevent sleep in those cases.
- Browser lifecycle and asynchronous requests can race with stop, reset, or completion → reconcile against current timer activity after requests resolve and release stale sentinels.
- Browsers may throttle work while the page is hidden → retain existing deadline-based timer behavior; wake-lock reacquisition does not promise background execution.
