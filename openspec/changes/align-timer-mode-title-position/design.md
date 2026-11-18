# Design

## Context

The heading currently relies on a flex row whose height is determined by its visible children. Stopwatch hides the settings button, so the row is only the title height. Intervals and Tabata show a 2.75rem settings button, making the row taller and vertically offsetting the title.

## Goals / Non-Goals

**Goals:**
- Keep mode titles at an identical position for all timer modes.
- Preserve the settings button's existing visibility and right alignment.
- Avoid changing navigation or timer behavior.

**Non-Goals:**
- Change the title text, typography, or reorder the timer modes.
- Change settings behavior or add a settings control to Stopwatch.

## Decisions

- Give the heading row a fixed or minimum height equal to the settings control's 2.75rem footprint, and keep title alignment centered within that row.
- Rationale: this removes the hidden-button height difference while preserving the existing left title and right settings layout.
- Alternative considered: keep the button in the layout but use `visibility: hidden` for Stopwatch. Rejected as unnecessary markup behavior because reserving the heading row's dimensions is sufficient and a fixed row is clearer.
- Alternative considered: absolute-position the title. Rejected because it is less robust across responsive padding and heading content.

## Risks / Trade-offs

- [Added vertical heading height] → The title occupies the same stable row, and 2.75rem is already the existing settings button footprint.
- [Responsive clipping] → Use the existing clamp-based page padding and verify portrait and landscape widths after implementation.

## Migration Plan

The change can be applied directly in `index.html`; no data migration or deployment step is required.
