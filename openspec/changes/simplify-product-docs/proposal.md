## Why

The docs follow a course template, and the course is over. Each story is copied into four files, so one new idea means four or five edits. Parallel branches would also conflict on the shared tables.

## What Changes

- **BREAKING** Remove personas. Their key rules move into the vision.
- **BREAKING** Write stories as "When…, I want to…, so that…".
- **BREAKING** Rewrite problem statements as situations, without names.
- **BREAKING** Drop story points and `sizing.md`.
- **BREAKING** Rename `one-pagers/` to `epics/`.
- Remove `drafts/`. Git keeps old versions.
- Keep only the next stories in the backlog.
- Remove the README status table. Derive status when needed.
- Let a story start as one line.
- Route new ideas by fit: amend a story, add a story, or add an epic.
- Let a change add details to its own story.
- Keep proposals and designs short and plain. Story designs get a sequence diagram.

## Capabilities

### New Capabilities

- `documentation/epics`: epics, stories, status, and routing.

### Modified Capabilities

- `documentation/doc-structure`: new layout.
- `documentation/product-vision`: adds principles and non-goals.
- `documentation/one-pagers`: retired into `epics`.
- `documentation/user-stories`: retired into `epics`.
- `documentation/personas`: retired.
- `documentation/requirements-sizing`: retired.
- `process/backlog-flow`: short backlog, no estimates.
- `process/vertical-slices`: a change may amend its story.
- `process/capability-layout`: slug from `docs/epics/`.
- `process/branching-and-releases`: no status table step.

## Impact

- Docs: all files under `docs/`.
- Config: `config.yaml` and the PR template.
- Story IDs don't change. No code exists.
