## MODIFIED Requirements

### Requirement: Epics Are Recognised And Split Before Implementation

A story too large to be delivered by a single change is an epic. During requirements definition an epic MAY stand as written; before it is ordered in the backlog or a change is proposed for it, it MUST be broken into simpler stories, each focused on a single aspect.

#### Scenario: An oversized story reaches the backlog

- **WHEN** a story sized at or above the splitting threshold is queued for implementation
- **THEN** it MUST first be decomposed into stories that can each be delivered by a single change

### Requirement: Implementation Status Is Derived From Specs

A story's implementation status SHALL be determined from the product capability specs in `openspec/specs/` and `openspec/changes/` — every capability outside the `documentation/` and `process/` domains — and MUST NOT be recorded as a hand-maintained marker on the story itself. A story is **implemented** when a requirement in a product capability spec under `openspec/specs/` cites its identifier; **in progress** when the only product requirement citing it belongs to an active change; and **not started** when no product requirement cites it.

#### Scenario: A story marker contradicts the specs

- **WHEN** a status marker written on a story disagrees with what the specs show
- **THEN** the specs are authoritative and the marker MUST be removed rather than corrected, because two independent records of the same fact will diverge again

#### Scenario: Someone asks what remains to be built

- **WHEN** a team member needs to know which stories are still outstanding
- **THEN** the answer MUST be obtainable from the specs and active changes without consulting any separate tracker

#### Scenario: A process or documentation spec mentions a story identifier

- **WHEN** a requirement under `documentation/` or `process/` names a story identifier, for example as an illustration
- **THEN** that mention MUST NOT affect the story's status, because those domains govern how the product is documented and built, not what it does

### Requirement: Specs Cite The Stories They Realize

Each requirement in a product capability spec SHALL cite the identifiers of the stories it realizes. A product requirement that realizes no documented story MUST either cite a story added for it or record why no story applies. Requirements in the `documentation/` and `process/` domains realize no story and are exempt.

#### Scenario: A capability spec is written for a documented story

- **WHEN** a requirement is written to implement a story
- **THEN** it MUST cite that story's identifier, so the link that makes status derivable exists in the direction that does not require editing the 1-pager

#### Scenario: Implementation introduces behavior no story describes

- **WHEN** a requirement is written that no story covers
- **THEN** either a story MUST be added to the appropriate 1-pager and cited, or the requirement MUST record that it is internal behavior with no user-facing story
