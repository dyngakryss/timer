# Design

## Context

The page is a single `index.html` with inline CSS and JavaScript. It currently selects between stopwatch and interval modes, uses a shared Settings dialog, and has separate timing state and rendering for each mode. See [proposal.md](./proposal.md) and the Tabata and navigation delta specs for the behavior contract.

## Goals / Non-Goals

**Goals:**
- Add Tabata without changing stopwatch or interval timing semantics.
- Keep Tabata configuration and session state independent from the other timer modes.
- Reuse existing timer presentation, settings dialog, deadline-based updates, controls, and carousel navigation patterns.

**Non-Goals:**
- Persisting settings between page sessions.
- Changing how the stopwatch or interval timer is configured or runs.
- Adding a rest period to the existing interval timer.

## Decisions

- Add a Tabata mode branch alongside stopwatch and interval. Keep its configuration and phase state separate rather than generalizing the existing interval state machine, which avoids changing established behavior for the two existing modes.
- Model Tabata phases explicitly as idle, startup countdown, work, rest, paused, and complete. Keep an absolute deadline for the active phase and the remaining duration when paused so timer refresh delays do not accumulate into phase drift.
- Track the current round and whether a paused session should resume work or rest. A work deadline transitions to rest for the same round; a rest deadline transitions to the next work round, or completes after the final rest.
- Add Tabata-only fields to the shared Settings dialog. Validate both durations using the interval minutes:seconds rules, rounds as a positive whole number, and startup countdown as non-negative whole-number seconds. Apply settings to the next session; reset to idle while retaining them.
- Extend the carousel to the ordered modes Stopwatch, Intervals, Tabata with no wrap. Keep a single active-mode guard that prevents navigation during the selected timer's active countdown or timed phases.
- Render the current Tabata phase and round progress with the existing full-screen readout and accessible timer labeling. A phase label is needed to distinguish work from rest while retaining the interval-style round presentation.

## Risks / Trade-offs

- [Risk] Confusing paused phase state with the phase that should start after a transition → Store the paused phase and remaining milliseconds separately from the active phase deadline.
- [Risk] A long timer refresh delay could shorten a subsequent work/rest period → Advance from absolute phase deadlines and carry elapsed time across transitions rather than restarting each phase at the time of the next render.
- [Risk] Adding a third mode may accidentally alter existing navigation behavior → Test the fixed order, endpoint behavior, and active-mode guard for all three modes.

## Migration Plan

No persisted data needs migration. Tabata settings default to the documented preset and startup countdown defaults to zero. Existing stopwatch and interval settings remain unchanged.
