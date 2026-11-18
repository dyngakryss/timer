# Design

## Context

The page is a single static `index.html`. Its `main` currently has carousel and region semantics, receives keyboard and swipe events, and wraps the mode heading, readout, and controls. `switchMode` updates the visible heading and mode state; `currentTimerIsActive` already blocks switching during active timer phases. A shared dialog click handler currently closes whenever the dialog itself is the event target.

## Goals / Non-Goals

**Goals:**
- Add an accessible visible mode selector while retaining existing navigation shortcuts and timer controls.
- Keep mode selection, title, tab state, and timer active-state behavior synchronized.
- Avoid repeating the active mode as a visible heading while preserving its accessible section label.
- Correct the main/section semantics and dialog backdrop hit-testing without adding dependencies.
- Keep the controls usable in the existing small-height landscape layout.

**Non-Goals:**
- Change timer state transitions, audio, settings values, or other timer behavior.
- Redesign the overall page or introduce a framework or test dependency.

## Decisions

- Replace the carousel identity with one native `main` landmark and a mode-labeled timer `section`. Keep the main focusable so the existing ArrowLeft/ArrowRight shortcut can remain available on the timer interface. Remove the role and carousel description that override the main landmark.
- Add a visible tablist with one tab per mode. Use the existing mode switch path for activation, keep the selected tab and document title in sync, and use roving focus with non-wrapping arrow navigation. Keep the existing interface arrow shortcut separate from tablist key handling, and retain the main swipe listener.
- Keep the mode heading visually hidden while retaining it as the timer section's accessible label; the selected tab provides the visible mode name.
- Drive tab disabled state from the same active-state condition that guards mode changes, including startup countdowns and Tabata work/rest. Preserve selection state while disabled; re-enable tabs when the current timer can be switched.
- Move the existing carousel-targeted layout selectors to the plain page container, and style the tab row compactly using existing button conventions. Use the small-height landscape media query to reduce tab spacing and text size rather than changing the timer layout.
- For dialog clicks, compare the event's client coordinates with the dialog's `getBoundingClientRect()` and close only when the point lies outside that rectangle. Checking the target alone cannot distinguish dialog padding from a backdrop click.

Alternatives considered: keeping carousel semantics would preserve the current interaction framing but continue to override the main landmark; replacing swipe and arrow behavior with tabs would remove existing shortcuts; closing only when the event target differs from the dialog would not resolve clicks on its padding.

## Risks / Trade-offs

- [The additional tab row could crowd short landscape viewports] → Keep styling compact and validate the small-height landscape layout with all tabs and timer controls visible.
- [Tablist and existing arrow shortcuts could both react to the same key event] → Handle tablist keys at the tablist and retain the interface shortcut's existing direct-target check.
- [Dialog bounds can change with viewport or content size] → Read `getBoundingClientRect()` at click time rather than caching its dimensions.

## Migration Plan

No persisted data or external interfaces need migration. Update the single page in place; reverting the page changes restores the previous behavior.

## Open Questions

None.
