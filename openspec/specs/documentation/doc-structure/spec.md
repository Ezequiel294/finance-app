## Purpose

Defines where the product's documentation lives, how it is named and indexed, and how references between documents stay valid.

## Requirements

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

### Requirement: Documentation Index

`docs/README.md` SHALL exist and list every document under `docs/` with a one-line description of what it covers.

#### Scenario: A document is added, renamed, or removed

- **WHEN** any file under `docs/` is created, renamed, or removed
- **THEN** `docs/README.md` MUST be updated in the same change, so the index never references a missing file and never omits an existing one

### Requirement: Undecided Product Name Placeholder

Until the product name is chosen, documents SHALL refer to the product using the single placeholder token `{{PRODUCT_NAME}}`. No other spelling, working title, or invented name may be used.

#### Scenario: Product name is chosen

- **WHEN** the final product name is selected
- **THEN** every occurrence of `{{PRODUCT_NAME}}` across `docs/` MUST be replaced in one pass, and the index MUST record the chosen name

#### Scenario: An ad-hoc name appears in a document

- **WHEN** a document introduces a working product name instead of the placeholder
- **THEN** it MUST be replaced with `{{PRODUCT_NAME}}`, so a single later substitution remains sufficient

### Requirement: References Resolve

Every story ID mentioned in a document, a spec, or a change SHALL exist in an epic. Every document listed in the index SHALL exist.

#### Scenario: A reference names a story that does not exist

- **WHEN** a document, spec, or change mentions a story ID that no epic contains
- **THEN** the mention MUST be fixed, or the story MUST be added to the right epic
