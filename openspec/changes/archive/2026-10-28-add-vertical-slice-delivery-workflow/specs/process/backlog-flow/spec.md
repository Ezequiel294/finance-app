## Purpose

Defines how work is ordered and limited without sprints: an ordered backlog that never records status, a limit on active stories per person, the conditions a story must meet before work starts and before it counts as done, and spikes as the way unverified assumptions are settled.

## ADDED Requirements

### Requirement: Ordered Backlog

`docs/backlog.md` SHALL list, in the order they are to be taken up, the identifiers of every story that is not yet implemented, not withdrawn, and not replaced by a split. It MUST NOT record any story's status. When a change is archived, the story it realized SHALL be removed from the backlog in the same change.

#### Scenario: A status marker is added to the backlog

- **WHEN** an entry in `docs/backlog.md` is marked in progress, done, or with any other status
- **THEN** the marker MUST be removed, because status is derived from the specs and a second record of it will drift

#### Scenario: The backlog lists an implemented story

- **WHEN** the backlog lists a story that a product capability spec in `openspec/specs/` already cites
- **THEN** the specs are authoritative and the entry MUST be removed

#### Scenario: A story is added to a 1-pager

- **WHEN** a new story is written into a 1-pager, including one created by splitting a larger story
- **THEN** its identifier MUST be added to the backlog in the same change, at its intended position or under the unordered heading, and a story it replaces by splitting MUST be removed

### Requirement: One Active Story Per Person

Each person SHALL have at most one active story change at a time.

#### Scenario: A person wants to start a second story

- **WHEN** a person has an active story change and wants to start another
- **THEN** the active change MUST be finished first, unless it is blocked on something outside that person's control, in which case the blocker MUST be recorded under Open Questions in that change's `design.md` before another story is started

### Requirement: Definition Of Ready

A change SHALL NOT be proposed for a story until all of the following hold: the story carries detail bullets; it carries an estimate and is not an unsplit story sized at 13; every unverified assumption in its 1-pager that the story depends on has been verified or refuted; and every story it depends on is implemented.

#### Scenario: The story depends on an unverified assumption

- **WHEN** the next story in the backlog relies on an assumption its 1-pager marks unverified
- **THEN** a spike MUST settle that assumption before a change is proposed for the story

#### Scenario: The story depends on a story not yet implemented

- **WHEN** the next story in the backlog needs behavior that another, unimplemented story delivers
- **THEN** that other story MUST be taken up first, and the backlog reordered to reflect it

### Requirement: Definition Of Done

A story SHALL be done only when all of the following hold:
- every task in its change is complete and every automated test passes;
- `openspec validate --strict` passes for the change;
- every non-functional requirement in its 1-pager that applies to the story is met, or deferred to a follow-up story recorded in that 1-pager;
- `docs/architecture.md` is updated if the change made a structural decision;
- the change is archived, the `docs/README.md` status table is refreshed, and the story is removed from the backlog, all on the work branch;
- the work branch is merged into `develop` and the merge commit is tagged.

#### Scenario: A non-functional requirement cannot be met within the story

- **WHEN** an applicable non-functional requirement cannot be met within the scope of the story
- **THEN** a follow-up story MUST be added to the 1-pager and the backlog, and the change's `design.md` MUST name it, so that the deferral is visible rather than silent

#### Scenario: Code is merged before its change is archived

- **WHEN** a story's implementation reaches `develop` while its change is still active
- **THEN** the story is not done, and the archive, status refresh, and backlog update MUST follow in a further pull request

### Requirement: Spikes Settle Unverified Assumptions

A spike SHALL be a time-boxed investigation of one unverified assumption, with its time box set before it starts. Its outcome SHALL be recorded in the 1-pager's ASSUMPTIONS as verified or refuted, with the source and the date. A spike is not an OpenSpec change, and code written during a spike MUST NOT be merged.

#### Scenario: A spike refutes an assumption

- **WHEN** a spike shows an assumption is false
- **THEN** the assumption MUST be updated with the finding, and every story that depended on it MUST be re-examined and re-sized, split, or withdrawn

#### Scenario: A spike runs out of time

- **WHEN** a spike reaches its time box without settling the assumption
- **THEN** what was learned and what remains unknown MUST be recorded against the assumption, which stays unverified
