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
The stopwatch SHALL allow the user to start or resume timing, stop timing without clearing elapsed time, and reset elapsed time to zero. Starting a new timing attempt from zero SHALL begin a fixed 10-second countdown; starting after pausing SHALL resume immediately without another countdown.

#### Scenario: Start timing
- **WHEN** the user activates Start while the stopwatch is at zero and stopped
- **THEN** the stopwatch displays a 10-second startup countdown before elapsed timing begins

#### Scenario: Stop and resume timing
- **WHEN** the user activates Stop while the stopwatch is running and later activates Start
- **THEN** the stopwatch pauses at its elapsed time and resumes from that time without counting the paused interval or repeating the startup countdown

#### Scenario: Reset timing
- **WHEN** the user activates Reset
- **THEN** the stopwatch stops and displays 00:00

### Requirement: Show countdown before stopwatch timing
Starting the stopwatch from zero SHALL display a 10-second countdown in minutes and seconds, then automatically begin stopwatch timing at 00:00 when the countdown reaches zero.

#### Scenario: Countdown reaches zero
- **WHEN** the 10-second countdown reaches zero
- **THEN** stopwatch timing begins from 00:00

#### Scenario: Cancel countdown with Stop
- **WHEN** the user activates Stop during the startup countdown
- **THEN** the countdown is cancelled, the stopwatch remains stopped at 00:00, and Start is available to begin a fresh 10-second countdown

#### Scenario: Cancel countdown with Reset
- **WHEN** the user activates Reset during the startup countdown
- **THEN** the countdown is cancelled, the stopwatch remains stopped at 00:00, and the next start uses a fresh 10-second countdown

### Requirement: Provide audible cues for stopwatch startup
The stopwatch SHALL play one short beep when each of 3, 2, and 1 seconds remains in its startup countdown, then play a 0.9-second beep that is slightly louder and lower-pitched when stopwatch timing begins.

#### Scenario: Hear final countdown cues
- **WHEN** the startup countdown displays 3, 2, and 1 seconds remaining
- **THEN** one short beep plays at each displayed value

#### Scenario: Hear the stopwatch start cue
- **WHEN** the startup countdown completes and stopwatch timing begins
- **THEN** one 0.9-second beep plays at a slightly lower pitch and slightly louder than the short countdown beeps

### Requirement: Adapt the stopwatch layout to mobile and tablet viewports
The stopwatch page SHALL use a borderless layout that lets the timer display occupy the available screen space while keeping the timer readable and all controls usable on mobile phones and tablets in portrait and landscape orientations, without horizontal overflow or clipped timer controls.

#### Scenario: Mobile portrait layout
- **WHEN** the page is viewed on a mobile phone in portrait orientation
- **THEN** the timer uses the available screen space, remains readable, and all controls fit within the viewport and can be activated

#### Scenario: Mobile landscape layout
- **WHEN** the page is viewed on a mobile phone in landscape orientation
- **THEN** the timer uses the available screen space while remaining visible with all controls usable within the viewport height and width

#### Scenario: Tablet portrait and landscape layouts
- **WHEN** the page is viewed on a tablet in portrait or landscape orientation
- **THEN** the layout adapts to the available space, keeps the timer display as large as practical, and displays all controls without horizontal overflow or clipping

### Requirement: Present stopwatch startup countdown in a blinking overlay
During its fixed 10-second startup countdown, the stopwatch SHALL show a centered overlay above its interface with only the remaining whole-second number from 10 through 1. The number SHALL be large and bold, the surrounding interface SHALL be subdued, and the existing stop and reset controls SHALL remain usable.

#### Scenario: Show the stopwatch countdown overlay
- **WHEN** a new stopwatch startup countdown begins
- **THEN** a centered overlay displays only the remaining number from 10 through 1 in large, bold type over a subdued interface

#### Scenario: Blink between stopwatch countdown numbers
- **WHEN** the displayed whole-second value advances during the startup countdown
- **THEN** the current number briefly fades or disappears before the next number appears

#### Scenario: Cancel the stopwatch countdown from the overlay
- **WHEN** the user activates Stop or Reset while the overlay is shown
- **THEN** the countdown is cancelled according to the existing stopwatch timing behavior
