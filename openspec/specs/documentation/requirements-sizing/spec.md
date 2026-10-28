## Purpose

Defines the effort metric used to size functional requirements, the scale and baseline it is measured against, and the rationale that must accompany every estimate.

## Requirements

### Requirement: Sizing Metric

Effort SHALL be estimated in **story points** — an arbitrary, relative measure — and the same metric MUST be used for every story across every 1-pager of a product. Person-hours and person-days MUST NOT be mixed into the estimates.

#### Scenario: A 1-pager sizes in a different unit

- **WHEN** a 1-pager expresses effort in hours, days, or any unit other than story points
- **THEN** it MUST be re-sized in story points so estimates remain comparable across the product

### Requirement: Sizing Scale

Sizes SHALL be drawn from the modified Fibonacci scale: 1, 2, 3, 5, 8, 13. No other value may be assigned.

#### Scenario: An off-scale estimate is assigned

- **WHEN** a story is assigned a value not on the scale
- **THEN** it MUST be moved to the nearest scale value, with the rationale updated to justify the choice

### Requirement: Published Baseline Anchor

Each product's `sizing.md` SHALL name one story as the baseline anchor and state its point value. Every other estimate MUST be made by comparison against that anchor.

#### Scenario: Sizing is performed with no anchor named

- **WHEN** estimates are assigned before a baseline anchor is published
- **THEN** the anchor MUST be chosen and published first, and the estimates re-checked against it

#### Scenario: The anchor is re-sized

- **WHEN** the baseline anchor's own value is changed
- **THEN** every estimate derived from it MUST be re-examined, since all sizes are relative to the anchor

### Requirement: Estimation Dimensions

Every estimate SHALL be formed by considering four dimensions: the **size** of the task, its **complexity**, the **technology** required, and the **unknowns** in the work.

#### Scenario: An estimate considers only volume of work

- **WHEN** a rationale accounts for size alone and ignores complexity, technology, or unknowns
- **THEN** it MUST be re-assessed across all four dimensions

### Requirement: Rationale Is Mandatory

Every sized story SHALL carry a written rationale naming which dimensions drove the number and what it was compared against. A size with no rationale is incomplete.

#### Scenario: A size is recorded without justification

- **WHEN** a story is assigned a point value with no stated reasoning
- **THEN** the rationale MUST be written before the 1-pager is considered complete

### Requirement: Splitting Threshold

A story sized at 13 points SHALL be treated as too large to estimate reliably and MUST be split into smaller stories, each sized independently.

#### Scenario: A story is sized at 13

- **WHEN** a story receives a size of 13
- **THEN** it MUST be decomposed, and both the decomposition and the resulting sizes recorded

### Requirement: Stated Estimate Uncertainty

`sizing.md` SHALL state that these are first-pass relative estimates made from an incomplete requirements definition by a team with no velocity history, and that initial estimates of this kind are expected to be substantially wrong and re-estimated as understanding improves.

#### Scenario: Estimates are presented as commitments

- **WHEN** sizing is presented as a schedule, a delivery date, or a commitment
- **THEN** it MUST be corrected to a relative estimate accompanied by the uncertainty statement

### Requirement: Cross-Document Consistency

Two stories assigned the same size within a product SHALL represent comparable effort, regardless of which 1-pager they appear in.

#### Scenario: Equal sizes describe plainly unequal work

- **WHEN** review finds two equally sized stories that clearly differ in effort
- **THEN** one MUST be re-sized and its rationale updated to restore comparability across the product
