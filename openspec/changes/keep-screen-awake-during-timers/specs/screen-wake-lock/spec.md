# Spec Delta

## Purpose

Keeps the device display awake while a user relies on an active timer, across Stopwatch, Intervals, and Tabata modes.

## ADDED Requirements

### Requirement: Keep the display awake while a timer is active
In browsers that support screen wake locks, the timer page SHALL keep the display awake while any timer is actively counting, including a startup countdown.

#### Scenario: Keep the display awake during Stopwatch timing
- **WHEN** the Stopwatch is running or its startup countdown is active
- **THEN** the timer page keeps the display awake

#### Scenario: Keep the display awake during Interval timing
- **WHEN** an Interval round or its startup countdown is active
- **THEN** the timer page keeps the display awake

#### Scenario: Keep the display awake during Tabata timing
- **WHEN** a Tabata work period, rest period, or startup countdown is active
- **THEN** the timer page keeps the display awake

### Requirement: Release the display wake lock when timing is inactive
The timer page SHALL release its display wake lock when the selected timer is no longer actively counting.

#### Scenario: Release after stopping or pausing
- **WHEN** the user stops or pauses an active timer
- **THEN** the timer page releases the display wake lock

#### Scenario: Release after reset or completion
- **WHEN** the user resets a timer or an interval or Tabata session completes
- **THEN** the timer page releases the display wake lock

### Requirement: Restore the display wake lock when an active timer returns to view
When a browser releases the display wake lock because the page is hidden, the timer page SHALL reacquire it when the page becomes visible again if a timer is still actively counting.

#### Scenario: Return to an active timer
- **WHEN** the page becomes visible while a timer is actively counting
- **THEN** the timer page keeps the display awake again

### Requirement: Continue timing when a display wake lock is unavailable
If the browser does not support a display wake lock or cannot grant one, the timer page SHALL continue normal timer operation.

#### Scenario: Wake lock is unsupported or unavailable
- **WHEN** a timer starts in a browser that does not support a display wake lock or the request cannot be granted
- **THEN** the timer starts and runs without a display wake lock
