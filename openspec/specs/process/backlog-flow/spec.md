# process/backlog-flow Specification

## Purpose
Defines how work is ordered and limited without sprints: an ordered backlog that never records status, a limit on active stories per person, the conditions a story must meet before work starts and before it counts as done, and spikes as the way unverified assumptions are settled.

## Requirements

### Requirement: One Active Story Per Person

Each person SHALL have at most one active story change at a time.

#### Scenario: A person wants to start a second story

- **WHEN** a person has an active story change and wants to start another
- **THEN** the active change MUST be finished first, unless it is blocked on something outside that person's control, in which case the blocker MUST be recorded under Open Questions in that change's `design.md` before another story is started

### Requirement: Definition Of Ready

A change SHALL NOT be proposed for a story until all of these are true:
- the story has detail bullets;
- the story can be delivered by one change;
- every unverified assumption in its epic that the story depends on has been checked and marked verified or refuted;
- every story it depends on is implemented.

#### Scenario: The story is too large for one change

- **WHEN** the next story in the backlog is judged too big for one change
- **THEN** it MUST be split before a change is proposed, and the backlog MUST be updated with the stories that replace it

#### Scenario: The story depends on an unverified assumption

- **WHEN** the next story in the backlog depends on an assumption its epic marks unverified
- **THEN** a spike MUST settle that assumption before a change is proposed for the story

#### Scenario: The story depends on a story not yet implemented

- **WHEN** the next story in the backlog needs behavior that another story, not yet built, delivers
- **THEN** that other story MUST be taken up first, and the backlog MUST be reordered to show it

### Requirement: Definition Of Done

A story SHALL be done only when all of these are true:
- every task in its change is complete, and every automated test passes;
- `openspec validate --strict` passes for the change;
- every non-functional requirement in its epic that applies to the story is met, or is deferred to a follow-up story written in that epic;
- `docs/architecture.md` is updated, if the change made a structural decision;
- the change is archived, and the story is removed from the backlog if it is listed there, both on the work branch;
- the work branch is merged into `develop`, and the merge commit is tagged.

#### Scenario: A non-functional requirement cannot be met within the story

- **WHEN** a non-functional requirement that applies can't be met within the story
- **THEN** a follow-up story MUST be added to the epic, and the change's `design.md` MUST name it, so the deferral is visible

#### Scenario: Code is merged before its change is archived

- **WHEN** a story's code reaches `develop` while its change is still active
- **THEN** the story is not done, and the archive and backlog update MUST follow in another pull request

### Requirement: Spikes Settle Unverified Assumptions

A spike SHALL be a short, time-boxed investigation of one unverified assumption. Its time limit SHALL be set before it starts. Its result SHALL be written in the epic's ASSUMPTIONS as verified or refuted, with the source and the date. A spike is not an OpenSpec change. Code written during a spike MUST NOT be merged.

#### Scenario: A spike refutes an assumption

- **WHEN** a spike shows an assumption is false
- **THEN** the assumption MUST be updated with the finding, and every story that depended on it MUST be checked again and then rewritten, split, or withdrawn

#### Scenario: A spike runs out of time

- **WHEN** a spike reaches its time limit without settling the assumption
- **THEN** what was learned, and what is still unknown, MUST be written down against the assumption, which stays unverified

### Requirement: Backlog Lists What Comes Next

`docs/backlog.md` SHALL list the IDs of the stories chosen to be worked on next, in the order they will be taken up. Each entry SHALL say why it is in that position.

The backlog SHALL NOT list every story. A story that isn't in the backlog simply has no order yet, and you find it in its epic. The backlog MUST NOT record any story's status. When a change is archived, the story it built SHALL be removed from the backlog in the same change.

#### Scenario: A status marker is added to the backlog

- **WHEN** an entry in `docs/backlog.md` is marked "in progress", "done", or with any other status
- **THEN** the marker MUST be removed, because status comes from the specs and a second record of it will drift

#### Scenario: The backlog lists an implemented story

- **WHEN** the backlog lists a story that a product spec in `openspec/specs/` already cites
- **THEN** the specs are right, and the entry MUST be removed

#### Scenario: A story is added to the backlog

- **WHEN** a story is put in the backlog
- **THEN** if it has no detail bullets, they MUST be written in its epic in the same edit, and the entry MUST say why it is at that position

#### Scenario: A story in the backlog is split

- **WHEN** a story in the backlog is split
- **THEN** its entry MUST be replaced by the stories that replace it, each at the position it should have
