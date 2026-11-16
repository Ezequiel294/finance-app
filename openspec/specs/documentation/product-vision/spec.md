## Purpose

Defines how the product vision, its principles, and its non-goals are written, and how every epic and story is checked against them.

## Requirements

### Requirement: Vision Answers Three Questions

The vision SHALL answer, without requiring any other document: what the product is and what makes it different from competing products; who the target users and customers are; and why customers would choose it.

#### Scenario: Vision is reviewed for completeness

- **WHEN** a reader who has seen no other project document reads only the vision
- **THEN** they MUST be able to state the product's what, who, and why

### Requirement: Vision Length And Tone

The vision SHALL be a short statement, not a specification. It MUST NOT list features, screens, data models, or technologies. Principles are rules for the whole product, not features.

#### Scenario: Vision drifts into a feature list

- **WHEN** the vision statement or a principle lists specific features or technical parts
- **THEN** those details MUST be removed from the vision and moved into the epics that cover them

### Requirement: Vision Governs Feature Inclusion

Every epic and story SHALL be checked against the vision, including its principles and non-goals. If the vision doesn't support a story, the story MUST be dropped, or the vision MUST be deliberately changed first.

#### Scenario: A proposed feature falls outside the vision

- **WHEN** someone proposes a story the current vision doesn't support
- **THEN** either the story is dropped, or the vision is changed first, in its own commit whose message says what changed and why

### Requirement: Vision States Principles And Non-Goals

`docs/vision.md` SHALL contain two sections:
- **Principles**: rules every epic and story must follow across the whole product. Each principle is a claim someone can check.
- **Non-goals**: the user types and features the product deliberately leaves out, each with its reason.

#### Scenario: A story conflicts with a principle

- **WHEN** a story would make the product unusable without a linked account, useless until someone sets it up, or break any other principle
- **THEN** the story MUST be changed to follow the principle, or the principle MUST be deliberately changed first

#### Scenario: A proposed capability matches a non-goal

- **WHEN** an idea serves a user type or feature listed as a non-goal
- **THEN** it MUST be rejected, unless someone first deliberately removes that non-goal and records why
