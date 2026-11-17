# interval-timer Specification

## Purpose

Provides a configurable countdown timer that runs a finite sequence of timed rounds and shows users which round is in progress.

## Requirements

### Requirement: Configure interval duration and round count
The interval timer SHALL let the user configure a positive whole-minute-and-second round duration and a positive whole-number total round count from the cogwheel Settings panel. Initial values SHALL be one minute and one round, and applied values SHALL remain in effect for the current page session.

#### Scenario: Apply interval settings
- **WHEN** the user enters a valid round duration and total round count in Settings and applies them
- **THEN** the values are used for the next interval timer start

#### Scenario: Reject invalid interval settings
- **WHEN** the user applies a zero or invalid duration, seconds outside 0 through 59, a fractional value, or a non-positive round count
- **THEN** the invalid settings are not accepted and the user can correct them

### Requirement: Count down and advance through interval rounds
The interval timer SHALL count down each configured round in minutes and seconds, show the current round out of the configured total, automatically begin the next round at full duration when one remains, and stop at zero after the final round.

#### Scenario: Start an interval session
- **WHEN** the user starts an interval timer while it is reset
- **THEN** the display counts down the configured duration and identifies the first round as 1 of the configured total

#### Scenario: Advance to the next round
- **WHEN** a round reaches zero and more configured rounds remain
- **THEN** the current round increases by one and its countdown begins immediately without a rest interval

#### Scenario: Complete the final round
- **WHEN** the final configured round reaches zero
- **THEN** the timer stops at zero and the displayed round count shows all configured rounds complete

### Requirement: Pause, resume, and reset interval timing
The interval timer SHALL let the user pause the current round without losing its remaining time or round progress, resume from that point, and reset the session without changing its configured settings.

#### Scenario: Pause and resume a round
- **WHEN** the user stops the interval timer during a round and later starts it again
- **THEN** the countdown resumes from the remaining time in that round without advancing the round during the pause

#### Scenario: Reset an interval session
- **WHEN** the user resets the interval timer
- **THEN** timing stops, round progress clears, the display returns to the configured round duration, and the settings remain available for the next start
