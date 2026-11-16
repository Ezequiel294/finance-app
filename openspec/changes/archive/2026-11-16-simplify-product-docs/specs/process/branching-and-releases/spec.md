## MODIFIED Requirements

### Requirement: Specs And Code Arrive Together

For a story change, two steps SHALL be committed on the work branch before it is merged: archiving the change, and removing the story from the backlog if it is listed there. This way `develop` gets the code and the updated specs in the same merge.

#### Scenario: A story is merged without its archive commit

- **WHEN** a story's work branch is merged while its change is still active
- **THEN** the story shows as in progress on `develop` even though it is built, and the archive MUST follow in another pull request
