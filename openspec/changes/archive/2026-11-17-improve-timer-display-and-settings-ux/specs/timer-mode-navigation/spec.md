# Spec Delta

## MODIFIED Requirements

### Requirement: Navigate timer modes with horizontal swipes and keyboard arrows
The timer page SHALL let users move between the stopwatch and interval timer by swiping horizontally or by using the left and right arrow keys when the timer-mode carousel has keyboard focus. The currently selected timer mode SHALL be identifiable to assistive technology, without visible carousel instructions or timer-position text.

#### Scenario: Swipe to another timer mode
- **WHEN** the user swipes left or right while timer-mode navigation is allowed
- **THEN** the adjacent timer mode in that direction is selected and presented

#### Scenario: Navigate timer modes by keyboard
- **WHEN** the timer-mode carousel has keyboard focus and the user presses the left or right arrow key while navigation is allowed
- **THEN** the adjacent timer mode in that direction is selected and presented

#### Scenario: Show mode without carousel guidance or position text
- **WHEN** either timer mode is displayed
- **THEN** no visible carousel instruction or “Timer X of 2” position text is shown, and the selected timer mode remains identifiable to assistive technology
