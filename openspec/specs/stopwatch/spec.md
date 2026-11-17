# stopwatch Specification

## Purpose

Provides a simple browser-based stopwatch so users can measure elapsed time and control timing from a standalone page.

## Requirements

### Requirement: Display elapsed minutes and seconds
The stopwatch SHALL display elapsed time as minutes and seconds, with seconds ranging from 00 to 59 and minutes increasing as time elapses.

#### Scenario: Initial display
- **WHEN** the stopwatch page is opened
- **THEN** the elapsed time is displayed as 00:00

#### Scenario: Elapsed time advances
- **WHEN** the stopwatch is running
- **THEN** the displayed seconds advance with elapsed time and roll over into the minutes without resetting the elapsed total

### Requirement: Control stopwatch timing
The stopwatch SHALL allow the user to start or resume timing, stop timing without clearing elapsed time, and reset elapsed time to zero.

#### Scenario: Start timing
- **WHEN** the user activates Start while the stopwatch is stopped
- **THEN** the stopwatch begins counting from its displayed elapsed time

#### Scenario: Stop and resume timing
- **WHEN** the user activates Stop while the stopwatch is running and later activates Start
- **THEN** the stopwatch pauses at its elapsed time and resumes from that time without counting the paused interval

#### Scenario: Reset timing
- **WHEN** the user activates Reset
- **THEN** the stopwatch stops and displays 00:00

### Requirement: Adapt the stopwatch layout to mobile and tablet viewports
The stopwatch page SHALL remain readable and fully usable on mobile phones and tablets in portrait and landscape orientations, without horizontal overflow or clipped timer controls.

#### Scenario: Mobile portrait layout
- **WHEN** the page is viewed on a mobile phone in portrait orientation
- **THEN** the timer remains readable and all controls fit within the viewport and can be activated

#### Scenario: Mobile landscape layout
- **WHEN** the page is viewed on a mobile phone in landscape orientation
- **THEN** the timer and all controls remain visible and usable within the viewport height and width

#### Scenario: Tablet portrait and landscape layouts
- **WHEN** the page is viewed on a tablet in portrait or landscape orientation
- **THEN** the layout adapts to the available space, keeps the timer readable, and displays all controls without horizontal overflow or clipping
