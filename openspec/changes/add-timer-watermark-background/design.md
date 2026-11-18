# Design

## Context

The three timer modes share one `<main>` interface in `index.html`; each mode changes the content and layout within it. The existing countdown overlay is a separate, higher-layer presentation. The available logo asset is `spangahanboll.png` in the project root. See proposal.md for motivation and specs/ for the behavior contract.

## Goals / Non-Goals

**Goals:**
- Render one consistent watermark behind the shared interface for every timer mode.
- Preserve the existing readout, controls, responsive layout, and countdown overlay behavior.
- Keep the logo decorative and prevent it from intercepting pointer input.

**Non-Goals:**
- Change timer behavior, countdown visuals, or audio cues.
- Add a user setting to show, hide, or adjust the watermark.
- Rename or replace the existing image asset.

## Decisions

- Add the logo as a single, non-interactive visual layer attached to the shared timer interface rather than repeating markup for each mode. This covers Stopwatch, Intervals, and Tabata uniformly and avoids mode-switch synchronization.
- Center the logo, preserve its aspect ratio, prevent tiling, and constrain its size to the available viewport. Apply low opacity so it reads as a watermark rather than competing with timer content; keep foreground text and controls above it.
- Keep the startup countdown overlay above the watermark. This preserves the established overlay presentation and controls while allowing the background treatment to remain consistent across timer states. A separate background image or per-mode styling was considered but would duplicate behavior and risk inconsistent alignment.

## Risks / Trade-offs

- The logo could reduce timer contrast on some viewports → use low opacity, keep timer content above the image, and check contrast/readability on narrow and wide layouts.
- The logo could be clipped or compete with content on small screens → constrain its size responsively and preserve its aspect ratio.
- The startup overlay may visually dim or cover part of the watermark → retain the overlay's existing layering and verify both layers remain visually subordinate and usable.

## Migration Plan

No persisted data, APIs, or dependencies are involved. Add the shared background layer and its styling. Rollback consists of removing that layer and styling; timer modes and countdown behavior remain unchanged.
