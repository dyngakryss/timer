# Spec Delta

## MODIFIED Requirements

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
