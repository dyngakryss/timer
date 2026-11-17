# Design

## Context

The app is a single `index.html` with inline CSS and JavaScript. Both timer modes share one carousel shell and display; interval Settings currently represent duration as separate minute and second fields. See [proposal.md](./proposal.md) and the delta specs for the behavior contract.

## Goals / Non-Goals

**Goals:**
- Keep the shared page shell responsive while using the viewport for the timer display and controls.
- Preserve mode navigation, timer state, and accessible mode identification as visible helper text is removed.
- Parse and validate the interval duration as one minutes:seconds value.

**Non-Goals:**
- Changing timing, round progression, persistence, or mode-switching rules.
- Adding dependencies or splitting the single-page app into modules.

## Decisions

- Keep the shared shell and timer display; remove card decoration and constrain sizing with viewport-aware CSS rather than creating separate layouts for each mode. This preserves existing timer behavior and avoids duplicated styles.
- Present the interval current-round numeral and countdown as a horizontal pair, with the round numeral sized to match the clock. Keep the total-round context available without competing with the large numeric display. This is clearer than placing the round number below the timer, especially when vertical space is limited.
- Store the duration as total seconds after parsing a strict minutes-colon-two-seconds string. Keep the configured value in existing session state and format it back to `MM:SS` when populating Settings. This keeps timer logic independent of the input representation and avoids ambiguity from loose numeric parsing.
- Preserve the carousel's accessible labeling and keyboard focus behavior when removing visible navigation copy; do not rely on the removed position text to identify the selected timer.

## Risks / Trade-offs

- [Risk] Maximizing the clock can crowd controls on short landscape screens → Use available viewport dimensions for sizing and verify controls remain visible and usable in narrow and short layouts.
- [Risk] Strict duration formatting may reject values users expect to be accepted → Show a clear validation error and retain the invalid entry for correction.

## Migration Plan

No persisted data or external interfaces need migration. Replace the duration input in place; existing session defaults and timer state remain unchanged.
