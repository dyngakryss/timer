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

### Requirement: Configure interval startup countdown
The interval timer SHALL let the user configure a non-negative whole number of startup countdown seconds from the interval Settings panel. The initial setting SHALL be zero, and an applied value SHALL remain in effect for the current page session and be used for the next new interval session.

#### Scenario: Apply interval startup countdown
- **WHEN** the user enters a valid whole number of seconds in interval Settings and applies it
- **THEN** the value is used before the next new interval session starts

#### Scenario: Reject invalid interval startup countdown
- **WHEN** the user attempts to apply an empty, negative, fractional, or otherwise invalid countdown value
- **THEN** the value is not accepted and the user can correct it

#### Scenario: Use zero countdown by default
- **WHEN** the user has not configured an interval startup countdown
- **THEN** the countdown setting is zero and a new interval session starts immediately

### Requirement: Count down and advance through interval rounds
The interval timer SHALL count down each configured round in minutes and seconds, show the current round out of the configured total, automatically begin the next round at full duration when one remains, and stop at zero after the final round. When a positive startup countdown is configured, a new session SHALL count down before starting round 1; when the setting is zero, round 1 SHALL start immediately. The round status SHALL appear above the countdown at approximately 67% of its text size, show only the current and total values as “X of Y”, and not show a standalone large round numeral beside the countdown.

#### Scenario: Start an interval session
- **WHEN** the user starts an interval timer while it is reset
- **THEN** the display starts the configured startup countdown when it is positive, or counts down the configured round duration immediately when it is zero, and shows “1 of <total>” above it at approximately 67% of the countdown text size

#### Scenario: Count down before the first round
- **WHEN** the user starts a new interval session with a positive startup countdown configured
- **THEN** the display counts down the configured startup seconds in minutes and seconds, shows “1 of <total>”, and begins round 1 at its full configured duration when the countdown reaches zero

#### Scenario: Start immediately with zero startup countdown
- **WHEN** the user starts a new interval session with a zero startup countdown configured
- **THEN** round 1 begins immediately at its full configured duration

#### Scenario: Advance to the next round
- **WHEN** a round reaches zero and more configured rounds remain
- **THEN** the current round increases by one, the status above the countdown updates to “<current> of <total>”, and the next countdown begins immediately without a rest interval

#### Scenario: Complete the final round
- **WHEN** the final configured round reaches zero
- **THEN** the timer stops at zero and the status above the countdown shows “<total> of <total>” without additional text

#### Scenario: Keep round information accessible
- **WHEN** an interval round or its startup countdown is displayed
- **THEN** only the current and total values in “<current> of <total>” format appear above the countdown, the separate large round numeral is absent, and the status remains accessible to assistive technology

### Requirement: Pause, resume, and reset interval timing
The interval timer SHALL let the user cancel a startup countdown, pause a round without losing its remaining time or round progress, resume a paused round without repeating the startup countdown, and reset the session without changing its configured settings.

#### Scenario: Stop during the startup countdown
- **WHEN** the user activates Stop during the interval startup countdown
- **THEN** the countdown is cancelled, the interval session remains unstarted at the configured round duration with round progress cleared, and Start is available to begin again

#### Scenario: Pause and resume a round
- **WHEN** the user stops the interval timer during a round and later starts it again
- **THEN** the countdown resumes from the remaining time in that round without advancing the round during the pause or repeating the startup countdown

#### Scenario: Reset during the startup countdown
- **WHEN** the user activates Reset during the interval startup countdown
- **THEN** the countdown is cancelled, round progress clears, the display returns to the configured round duration, and the configured startup countdown remains available for the next start

#### Scenario: Reset an interval session
- **WHEN** the user resets the interval timer
- **THEN** timing stops, round progress clears, the display returns to the configured round duration, and all configured settings remain available for the next session
