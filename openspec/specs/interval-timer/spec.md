# interval-timer Specification

## Purpose

Provides a configurable countdown timer that runs a finite sequence of timed rounds and shows users which round is in progress.

## Requirements

### Requirement: Configure interval duration and round count
The interval timer SHALL let the user configure a positive round duration with a text field labeled “Round duration (mm:ss)” and a positive whole-number total round count from the cogwheel Settings panel. The duration SHALL use minutes followed by a colon and exactly two seconds digits from 00 through 59, and SHALL be greater than zero. Initial values SHALL be one minute and one round, and applied values SHALL remain in effect for the current page session.

#### Scenario: Apply interval settings
- **WHEN** the user enters a valid duration in minutes:seconds format and a valid total round count in Settings and applies them
- **THEN** the values are used for the next interval timer start

#### Scenario: Reject invalid interval settings
- **WHEN** the user applies a malformed duration, seconds outside 00 through 59, a zero duration, or a non-positive or fractional round count
- **THEN** the invalid settings are not accepted and the user can correct them

#### Scenario: Identify the duration setting
- **WHEN** the user opens interval Settings
- **THEN** the duration is configured in one text field labeled “Round duration (mm:ss)” rather than separate minute and second fields

### Requirement: Count down and advance through interval rounds
The interval timer SHALL count down each configured round in minutes and seconds, show the current round out of the configured total, automatically begin the next round at full duration when one remains, and stop at zero after the final round.

#### Scenario: Start an interval session
- **WHEN** the user starts an interval timer while it is reset
- **THEN** the display counts down the configured duration, shows the current round number in clock-sized type to the left of the countdown, and identifies the first round as 1 of the configured total

#### Scenario: Advance to the next round
- **WHEN** a round reaches zero and more configured rounds remain
- **THEN** the current round increases by one and its countdown begins immediately without a rest interval

#### Scenario: Complete the final round
- **WHEN** the final configured round reaches zero
- **THEN** the timer stops at zero and the displayed round count shows all configured rounds complete

#### Scenario: Keep round information accessible
- **WHEN** an interval round is displayed
- **THEN** the current round number is visually positioned to the left of the countdown at the same size, and the current and total round values remain available as a secondary or accessible description

### Requirement: Pause, resume, and reset interval timing
The interval timer SHALL let the user pause the current round without losing its remaining time or round progress, resume from that point, and reset the session without changing its configured settings.

#### Scenario: Pause and resume a round
- **WHEN** the user stops the interval timer during a round and later starts it again
- **THEN** the countdown resumes from the remaining time in that round without advancing the round during the pause

#### Scenario: Reset an interval session
- **WHEN** the user resets the interval timer
- **THEN** timing stops, round progress clears, the display returns to the configured round duration, and the settings remain available for the next start
