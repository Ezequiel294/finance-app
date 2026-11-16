## ADDED Requirements

### Requirement: References Resolve

Every story ID mentioned in a document, a spec, or a change SHALL exist in an epic. Every document listed in the index SHALL exist.

#### Scenario: A reference names a story that does not exist

- **WHEN** a document, spec, or change mentions a story ID that no epic contains
- **THEN** the mention MUST be fixed, or the story MUST be added to the right epic

## MODIFIED Requirements

### Requirement: Separation Of Rules From Content

Files under `openspec/specs/` SHALL say how documents are written, read, and updated. They MUST NOT contain the documents themselves. All document content SHALL live under `docs/`.

#### Scenario: Document content written into a spec file

- **WHEN** an actual vision statement, epic, or story is written into a file under `openspec/specs/`
- **THEN** it MUST be moved to the matching file under `docs/`, so the spec keeps only the rules

#### Scenario: Document content written outside docs/

- **WHEN** a product document is created at the repository root or in some other folder
- **THEN** it MUST be moved under `docs/` before the work that created it counts as finished

### Requirement: Document Set Layout

The product's documentation SHALL live in `docs/`, with this layout:
- `README.md`: the index;
- `vision.md`;
- `backlog.md`: the stories to take up next, in order;
- `epics/`: one file per epic.

From the first product change on, `docs/` SHALL also contain `architecture.md`, which describes how the code is structured. Older versions of a document are kept by git history, not as copies in `docs/`.

#### Scenario: A document is placed outside the defined layout

- **WHEN** one of these documents is created at a path the layout doesn't define
- **THEN** it MUST be moved to its defined path, so readers always find each document where they expect it

#### Scenario: A superseded version is saved as a copy

- **WHEN** an older version of a document is saved as a separate file under `docs/`
- **THEN** the copy MUST be removed, and the reason for the change MUST go in the commit message instead

#### Scenario: The first product change is archived without an architecture document

- **WHEN** the first change that adds a product spec is archived and `docs/architecture.md` doesn't exist
- **THEN** the change is not finished, and `docs/architecture.md` MUST be written before it is merged

## REMOVED Requirements

### Requirement: Cross-Document Reference Integrity

**Reason**: It checked persona references, and personas are removed.
**Migration**: See **References Resolve**, which checks story IDs and index entries.

### Requirement: One-Pager File Naming

**Reason**: 1-pagers become epics.
**Migration**: See **Epic File Layout** in `documentation/epics`. Files move to `docs/epics/<NN>-<epic-slug>.md`. Slugs and numbers stay the same.

### Requirement: Implementation Status Index

**Reason**: The table was a saved copy of status, and the specs already determine status. It went out of date between refreshes. With parallel work, every archive edited the same rows and caused merge conflicts.
**Migration**: The table is removed from `docs/README.md`. Status is read from the specs when needed. See **Implementation Status Is Derived From Specs** in `documentation/epics`. The README explains how.

### Requirement: Superseded Versions Are Retained On Composition Change

**Reason**: Git history already keeps every older version, and commit messages can explain why something changed.
**Migration**: `docs/drafts/` is deleted. It can still be recovered from git history. When a change alters what a document says, its commit message explains what changed and why.
