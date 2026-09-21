## Purpose

Defines the format of the user stories that make up the functional requirements of a 1-pager, and that are reused later as product backlog items during development.

## ADDED Requirements

### Requirement: Story Format

Every functional requirement SHALL be written as a user story in the form: **As a** `<persona>`, **I want to** `<perform task>` **so that I can** `<description>` — or the equivalent **in order to** `<description>`.

#### Scenario: A requirement is written as a system statement

- **WHEN** a functional requirement is phrased as "The system shall…" or as a bare feature name
- **THEN** it MUST be rewritten in the story format with a named persona and a stated reason

#### Scenario: The justification clause is omitted

- **WHEN** a story states a role and a task but no "so that" or "in order to" clause
- **THEN** the clause MUST be added, because the reason is what lets a reader judge whether the task is the right solution

### Requirement: Stories Name A Defined Persona

The `<persona>` in a story SHALL be one of the personas defined in that product's `personas.md`. Generic roles such as "user" MUST NOT be used.

#### Scenario: A story names an undefined role

- **WHEN** a story's role is not a persona defined in `personas.md`
- **THEN** either the role MUST be replaced with a defined persona, or the persona MUST be added under the persona rules

### Requirement: Stories Describe One Thing

Each story SHALL set out a single thing the persona wants from the product.

#### Scenario: A story contains multiple wants

- **WHEN** a story joins several distinct capabilities with "and" or a list
- **THEN** it MUST be split into one story per capability

### Requirement: Supporting Detail Bullets

Each story MAY be followed by indented detail bullets that add specificity. These bullets SHALL elaborate the story they sit under and MUST NOT introduce a capability the story does not mention.

#### Scenario: A detail bullet introduces new functionality

- **WHEN** a detail bullet describes a capability absent from its parent story
- **THEN** that capability MUST be promoted to its own story

### Requirement: Epics Are Recognised And Split Before Implementation

A story too large to be implemented in a single sprint is an epic. During requirements definition an epic MAY stand as written; before it enters a backlog for implementation it MUST be broken into simpler stories, each focused on a single aspect.

#### Scenario: An oversized story reaches the backlog

- **WHEN** a story sized above the splitting threshold is queued for implementation
- **THEN** it MUST first be decomposed into stories that each fit within one sprint

### Requirement: Negative Stories Are Reframed

A story SHALL NOT be written in the negative form "I don't want…" in any document used as a product backlog, because a negative cannot be demonstrated by a system test. Such a need MUST be reframed as a positive statement of control the persona exercises.

#### Scenario: A constraint is expressed as a negative story

- **WHEN** a story states what the persona does not want the system to do
- **THEN** it MUST be reframed as the control the persona wants — for example, wanting to control and revoke what the system accesses — so it can be tested

### Requirement: Stories Avoid Implementation Prescription

A story SHALL describe what the persona wants to do, not how the system implements it. Naming a specific mechanism is permitted only where that mechanism is what the persona genuinely requires and both users and developers understand it.

#### Scenario: A story names a mechanism

- **WHEN** a story specifies a particular technology, library, or interface mechanism
- **THEN** it MUST be checked to determine whether the persona needs that specific mechanism or whether it stands for a more general need, and the more general need MUST be recorded when that is the case
