# Design

## Context

The stopwatch already tracks a configured countdown duration and a countdown deadline before elapsed-time timing begins. Interval mode currently starts round 1 immediately and uses `intervalPhase` for idle, running, paused, and complete states. See [proposal.md](./proposal.md) and the `interval-timer` delta for the behavior contract.

## Goals / Non-Goals

**Goals:**
- Add a separate interval startup countdown configuration to the existing shared Settings dialog.
- Represent the pre-session countdown distinctly from a running or paused interval round.
- Preserve the configured interval and round settings while starting, cancelling, pausing, resuming, or resetting.

**Non-Goals:**
- Adding a countdown before each round.
- Changing stopwatch countdown behavior, interval round progression, or the duration input format.

## Decisions

- Add an interval-specific configured countdown-seconds value, defaulting to zero, and expose its input only while Interval Settings is selected. Validate it as a non-negative whole number, consistently with the stopwatch field.
- Extend interval state with a countdown phase and deadline. On a new session, initialize the session’s duration and round count, then either enter countdown or start round 1 immediately. When the countdown deadline expires, begin round 1 at its full duration.
- Keep pause/resume distinct from startup countdown: Stop during countdown cancels the pending session to idle; Stop during a round preserves remaining round time as paused; Start from paused resumes directly. Reset returns to idle and retains all settings.
- Treat the countdown phase as active for the Stop control and mode-switch guard, so the selected interval mode cannot change while the startup countdown is running.
- Render startup remaining seconds through the existing minutes:seconds display while retaining the interval round status. This avoids separate visual timer paths.

## Risks / Trade-offs

- [Risk] Countdown completion may lose time if the browser throttles interval refreshes → Use an absolute deadline and transition based on the current time, consistent with the existing timer timing approach.
- [Risk] Treating countdown as inactive could permit a mode switch or leave Stop disabled → Include the countdown phase in active-state and control calculations.

## Migration Plan

No persisted data needs migration. The new setting defaults to zero, preserving immediate interval starts for users who do not configure it.
