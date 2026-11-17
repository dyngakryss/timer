# Spec Delta

## ADDED Requirements

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
