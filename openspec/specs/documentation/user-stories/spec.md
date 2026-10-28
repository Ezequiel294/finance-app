## Purpose

Defines the format of the user stories that make up the functional requirements of a 1-pager, and that are reused later as product backlog items during development.

## Requirements

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

### Requirement: Stable Story Identifiers

Every story SHALL carry an identifier of the form `<one-pager ordinal>-S<NN>`, unique across the product and assigned once. An identifier MUST NOT be reused, renumbered, or reassigned to a different story after it is issued.

#### Scenario: Stories are reordered within a 1-pager

- **WHEN** stories are reordered, inserted, or removed from a 1-pager
- **THEN** existing identifiers MUST keep their original values and new stories MUST take the next unused number, because other documents and specs reference stories by identifier

### Requirement: Stories Are Durable

A story SHALL NOT be deleted from its 1-pager once implemented. The 1-pager is a standing description of what the product is meant to do for its personas, and MUST remain readable as a complete account of that initiative.

#### Scenario: A story is implemented

- **WHEN** the functionality a story describes has been built
- **THEN** the story MUST remain in its 1-pager unchanged, because removing it would leave a PROBLEM section whose requirements no longer appear and would misrepresent the initiative to a new reader

#### Scenario: A 1-pager is read after most of its stories are built

- **WHEN** someone reads a 1-pager to understand an initiative
- **THEN** they MUST find every story that defines it, regardless of how much of it is already built

### Requirement: Implementation Status Is Derived From Specs

A story's implementation status SHALL be determined from the state of `openspec/specs/` and `openspec/changes/`, and MUST NOT be recorded as a hand-maintained marker on the story itself. A story is **implemented** when a requirement in `openspec/specs/` cites its identifier; **in progress** when the only requirement citing it belongs to an active change; and **not started** when no requirement cites it.

#### Scenario: A story marker contradicts the specs

- **WHEN** a status marker written on a story disagrees with what the specs show
- **THEN** the specs are authoritative and the marker MUST be removed rather than corrected, because two independent records of the same fact will diverge again

#### Scenario: Someone asks what remains to be built

- **WHEN** a team member needs to know which stories are still outstanding
- **THEN** the answer MUST be obtainable from the specs and active changes without consulting any separate tracker

### Requirement: Specs Cite The Stories They Realize

Each requirement in a capability spec SHALL cite the identifiers of the stories it realizes. A requirement that realizes no documented story MUST either cite a story added for it or record why no story applies.

#### Scenario: A capability spec is written for a documented story

- **WHEN** a requirement is written to implement a story
- **THEN** it MUST cite that story's identifier, so the link that makes status derivable exists in the direction that does not require editing the 1-pager

#### Scenario: Implementation introduces behavior no story describes

- **WHEN** a requirement is written that no story covers
- **THEN** either a story MUST be added to the appropriate 1-pager and cited, or the requirement MUST record that it is internal behavior with no user-facing story

### Requirement: Withdrawn Stories Are Marked, Not Deleted

A story decided against SHALL be marked withdrawn, with the reason and the date, and MUST remain in its 1-pager.

#### Scenario: A story is dropped from scope

- **WHEN** the team decides a story will not be built
- **THEN** it MUST be marked withdrawn with the reason, so the decision is visible to anyone who later asks why that capability is absent

#### Scenario: A withdrawn story is reinstated

- **WHEN** a withdrawn story is brought back into scope
- **THEN** its withdrawal note MUST be replaced with a note recording the reinstatement and its date, and the story keeps its original identifier
