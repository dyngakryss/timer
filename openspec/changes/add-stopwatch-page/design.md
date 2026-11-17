# Design

## Context

The project has no application code or established frontend stack. See proposal.md for the motivation and specs/stopwatch/spec.md for the behavior contract.

## Goals / Non-Goals

**Goals:**
- Keep the stopwatch usable as a standalone page without a build step or external dependencies.
- Keep elapsed time correct when browser rendering is delayed or throttled.

**Non-Goals:**
- Add lap recording, countdowns, persistence across page reloads, or a framework.

## Decisions

- Implement the page as a self-contained `index.html` with embedded styling and script. This keeps the requested HTML page directly openable and avoids introducing a toolchain or dependency for a single feature; separate assets can be considered if the page grows.
- Store elapsed duration and the time at which the current run began. Update the display periodically from the current timestamp and those values rather than incrementing a seconds counter on each display tick. This prevents delayed browser callbacks from accumulating timing drift; the display may refresh less frequently while backgrounded, but the elapsed value will catch up when updates resume.
- Treat Stop as pause and Start as start-or-resume; Reset stops timing and clears the duration. This aligns the controls with the specified behavior and avoids separate start and resume actions.

## Risks / Trade-offs

- Browser scheduling can delay visual updates in background tabs → calculate elapsed time from timestamps whenever rendering resumes.
- A standalone file may become harder to maintain if the page expands → keep the initial implementation focused and split assets only when justified.

## Migration Plan

No migration is required. Add the page at the project root and open it directly in a browser. Removing the page rolls back the change.
