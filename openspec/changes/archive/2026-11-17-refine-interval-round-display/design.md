# Design

## Context

The shared readout contains the clock and a separate interval round numeral; the current/total round status is rendered below the readout. See [proposal.md](./proposal.md) and the `interval-timer` delta for the requested behavior.

## Goals / Non-Goals

**Goals:**
- Keep the countdown as the primary visual element and move current/total round context above it.
- Retain existing round-status text and lifecycle updates without changing timer logic.

**Non-Goals:**
- Changing interval duration, round progression, pause/resume, or completion behavior.
- Changing the stopwatch display.

## Decisions

- Reuse the existing round-status element and position it before the clock within the interval readout flow. This keeps status updates and accessibility behavior in one place; a second status element would duplicate content and require extra synchronization.
- Set status typography relative to the clock at 67%, so it remains proportionate across the existing responsive clock sizes. Remove the separate numeral from the markup and render path rather than hiding it with styling.
- Keep the stopwatch layout unchanged by applying interval-specific presentation only when interval mode is selected.

## Risks / Trade-offs

- [Risk] Larger status strings such as completion text may take more horizontal space → Allow the label to wrap where needed and check narrow portrait and short landscape layouts.

## Migration Plan

No persisted data or external interfaces change. Existing interval round state and status messages remain unchanged.
