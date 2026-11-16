# process/vertical-slices Specification

## Purpose
Defines how a single user story is turned into working software: one change per story, its detail bullets carried into spec scenarios, and its implementation delivered as a sequence of thin vertical slices that are each tested, working, and reviewed before the next begins.

## Requirements

### Requirement: One Change Per Story

A change that adds or modifies product capability specs SHALL be driven by exactly one user story. The change SHALL be named `<story-id>-<slug>` in lowercase, and its proposal MUST name the story identifier it realizes.

#### Scenario: A change bundles several stories

- **WHEN** a proposed change would realize more than one story
- **THEN** it MUST be split into one change per story, because every story an active change cites is reported in progress until the whole change is archived, and a bundled change hides which of its stories are actually finished

#### Scenario: A change is named after its content rather than its story

- **WHEN** a story's change is named without the story identifier
- **THEN** it MUST be renamed to `<story-id>-<slug>`, so the change, its work branch, and its archive folder can each be traced back to the story by name alone

### Requirement: Story Detail Bullets Become Scenarios

Every detail bullet under the story a change realizes SHALL be carried into at least one `#### Scenario:` in the change's delta specs. Every scenario in those delta specs MUST trace to the story statement or to one of its detail bullets.

#### Scenario: A detail bullet has no scenario

- **WHEN** a detail bullet under the story is not covered by any scenario in the delta specs
- **THEN** a scenario MUST be added for it before tasks are written, because a bullet with no scenario has no test and will not be built

#### Scenario: A scenario traces to nothing in the story

- **WHEN** a scenario describes behavior that neither the story nor its detail bullets mention
- **THEN** it MUST be removed from the change, and if the behavior is genuinely needed, a story MUST be added for it to the appropriate 1-pager and taken up as its own change

### Requirement: Tasks Are Ordered Vertical Slices

A story change's `tasks.md` SHALL be a sequence of slices, each a task group headed `## <N>. Slice <N>: <observable behavior>`, followed by a final `Done` group. Each slice SHALL deliver one behavior that a persona or an automated test can observe, carrying it through every layer it needs. Slice boundaries SHALL be chosen per story when its tasks are written; no fixed size applies.

#### Scenario: Tasks are grouped by layer

- **WHEN** a task group covers a single layer for the whole story, such as all of the data model or all of the interface
- **THEN** the tasks MUST be regrouped into slices, because a layer built in full before anything uses it is integrated only at the end, which is exactly the risk slicing exists to remove

#### Scenario: A slice delivers nothing observable

- **WHEN** a slice's tasks produce no behavior a persona or test can observe on its own
- **THEN** it MUST be merged into the slice whose behavior needs it

### Requirement: Each Slice Leaves The Product Working

At the end of every slice the product SHALL build, every automated test in the repository SHALL pass, and the slice's behavior SHALL be demonstrable by following demo steps recorded in the slice's final task.

#### Scenario: A slice ends with a failing test or a broken build

- **WHEN** a slice's tasks are complete but the build fails or any test fails
- **THEN** the slice is not complete, and the next slice MUST NOT begin until it is

### Requirement: Tests Precede Implementation Within A Slice

Each slice SHALL begin with tasks that write automated tests for the scenarios it realizes. Those tests MUST fail before the slice's implementation tasks and pass after them.

#### Scenario: An implementation task precedes the slice's tests

- **WHEN** a slice lists implementation tasks ahead of the tests for its scenarios
- **THEN** the tasks MUST be reordered so the tests come first, because a test written after the code tends to describe the code rather than the scenario

### Requirement: Later Slices Test Their Interaction With Earlier Ones

Every slice after the first SHALL include at least one test that exercises its behavior together with behavior delivered by an earlier slice. Tests from earlier slices MUST continue to pass.

#### Scenario: A slice changes what an earlier slice produces

- **WHEN** a later slice deliberately changes behavior an earlier slice's test asserts
- **THEN** that test MUST be updated to the new expected behavior, citing the scenario that justifies the change, and MUST NOT be deleted or skipped to make the build pass

#### Scenario: A slice is tested only in isolation

- **WHEN** a slice after the first has tests only for its own behavior
- **THEN** a test MUST be added that exercises it together with an earlier slice, because slices that each work alone can still fail when combined

### Requirement: Each Slice Is Reviewed Before The Next Begins

Each slice SHALL be committed separately from every other slice. Generated scaffolding MAY be committed separately within its slice so that it can be read apart from hand-written code. Work on the next slice MUST NOT begin until the slice has been reviewed and accepted.

#### Scenario: Implementation is carried out by an assistant

- **WHEN** an assistant implements a slice
- **THEN** it MUST stop when the slice is complete and present the changes it made in each layer, the tests it added, and the slice's demo steps, and MUST wait for the review to be accepted before starting the next slice

#### Scenario: A slice is too large to review comfortably

- **WHEN** a reviewer judges a slice too large to read properly in one sitting
- **THEN** the remaining work MUST be split into smaller slices in `tasks.md` before implementation continues, because a review that cannot be done properly gets approved anyway, which is the same as no review

### Requirement: Foundations Are Built When A Slice Needs Them

No table, endpoint, screen, shared component, or infrastructure SHALL be built ahead of the slice that first needs it. The first slice of the first product change SHALL be a walking skeleton: the minimum of every layer, plus an automated test runner, carrying one behavior end to end.

#### Scenario: A task builds something no current slice uses

- **WHEN** a task produces something that no slice in the change requires
- **THEN** it MUST be removed, or moved into the slice that first needs it

### Requirement: Specs Are Corrected Before Code Diverges

When implementation shows that a change's specs, design, or tasks are wrong or incomplete, those artifacts SHALL be updated before the implementation moves past what they describe.

#### Scenario: Implementation needs behavior the spec does not describe

- **WHEN** a slice cannot be completed without behavior missing from the change's delta specs
- **THEN** the delta specs MUST be updated first, and if that behavior lies outside the story, a new story MUST be added to the appropriate 1-pager instead
