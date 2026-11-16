## MODIFIED Requirements

### Requirement: Tasks Are Ordered Vertical Slices

A story change's `tasks.md` SHALL be a list of slices, followed by a final `Done` group. Each slice is a task group with the heading `## <N>. Slice <N>: <observable behavior>`.

Each slice SHALL deliver one behavior that a person using the product, or an automated test, can see. It carries that behavior through every layer it needs. Where one slice ends and the next begins SHALL be decided per story, when its tasks are written. There is no fixed size.

#### Scenario: Tasks are grouped by layer

- **WHEN** a task group covers one layer for the whole story, such as the whole data model or the whole interface
- **THEN** the tasks MUST be regrouped into slices, because a layer built in full before anything uses it only gets connected at the end, and that late connection is the risk slicing exists to remove

#### Scenario: A slice delivers nothing observable

- **WHEN** a slice's tasks produce no behavior that a person or a test can see on its own
- **THEN** it MUST be merged into the slice whose behavior needs it

### Requirement: Story Detail Bullets Become Scenarios

Every detail bullet under the change's story SHALL become at least one `#### Scenario:` in the change's delta specs. Every scenario in those delta specs MUST trace back to the story itself or to one of its detail bullets.

#### Scenario: A detail bullet has no scenario

- **WHEN** a detail bullet under the story isn't covered by any scenario in the delta specs
- **THEN** a scenario MUST be added for it before tasks are written, because a bullet with no scenario gets no test and won't be built

#### Scenario: A scenario traces to nothing in the story

- **WHEN** a scenario describes behavior that neither the story nor its detail bullets mention
- **THEN** if the behavior fits the story's intent, a detail bullet MUST be added to the story in its epic, in the same change; otherwise the scenario MUST be removed, and if the behavior is really needed, a new story MUST be added to the right epic and taken up as its own change

### Requirement: Specs Are Corrected Before Code Diverges

When building shows that a change's specs, design, or tasks are wrong or incomplete, those files SHALL be fixed before the code goes beyond what they describe.

#### Scenario: Implementation needs behavior the spec does not describe

- **WHEN** a slice can't be finished without behavior that the change's delta specs don't describe
- **THEN** the delta specs MUST be updated first; if the behavior fits the story's intent, a detail bullet MUST also be added to the story in its epic; if it is outside the story, a new story MUST be added to the right epic instead
