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
