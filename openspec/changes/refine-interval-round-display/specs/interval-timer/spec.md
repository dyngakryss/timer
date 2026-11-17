# Spec Delta

## MODIFIED Requirements

### Requirement: Count down and advance through interval rounds
The interval timer SHALL count down each configured round in minutes and seconds, show the current round out of the configured total, automatically begin the next round at full duration when one remains, and stop at zero after the final round. The round status SHALL appear above the countdown at approximately 67% of its text size, and the standalone large round numeral beside the countdown SHALL not be shown.

#### Scenario: Start an interval session
- **WHEN** the user starts an interval timer while it is reset
- **THEN** the display counts down the configured duration and shows the first round as 1 of the configured total above it at approximately 67% of the countdown text size

#### Scenario: Advance to the next round
- **WHEN** a round reaches zero and more configured rounds remain
- **THEN** the current round increases by one, the status above the countdown updates to show the current and total round, and the next countdown begins immediately without a rest interval

#### Scenario: Complete the final round
- **WHEN** the final configured round reaches zero
- **THEN** the timer stops at zero and the status above the countdown shows all configured rounds complete

#### Scenario: Keep round information accessible
- **WHEN** an interval round is displayed
- **THEN** the current and total round status appears above the countdown, the separate large round numeral is absent, and the status remains accessible to assistive technology
