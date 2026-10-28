## Purpose

Defines where the product's documentation lives, how its files and directories are named, how the document index is maintained, and how a reader determines which documented requirements are already built.

## Requirements

### Requirement: Separation Of Rules From Content

Specification files under `openspec/specs/` SHALL define how documents are written, read, and updated. They MUST NOT contain document content. All document content SHALL live under `docs/`.

#### Scenario: Document content written into a spec file

- **WHEN** an actual vision statement, persona, or 1-pager body is written into a file under `openspec/specs/`
- **THEN** it MUST be moved to the corresponding file under `docs/`, leaving only the authoring rules in the spec

#### Scenario: Document content written outside docs/

- **WHEN** a product document is created at the repository root or in an ad-hoc directory
- **THEN** it MUST be relocated under `docs/` before the work that created it is considered complete

### Requirement: Document Set Layout

The product's documentation SHALL occupy `docs/` with this layout: `README.md` (the index), `vision.md`, `personas.md`, `sizing.md`, a `one-pagers/` directory, and a `drafts/` directory holding superseded versions.

#### Scenario: A document is placed outside the defined layout

- **WHEN** a document of one of these types is created at a path the layout does not define
- **THEN** it MUST be moved to its defined path, so every reader finds each document type where it is expected

### Requirement: One-Pager File Naming

Each 1-pager SHALL be one file at `docs/one-pagers/<NN>-<epic-slug>.md`, where `<NN>` is a zero-padded two-digit ordinal establishing reading order and `<epic-slug>` is kebab-case.

#### Scenario: Two 1-pagers claim the same ordinal

- **WHEN** a new 1-pager is added with an ordinal already in use
- **THEN** the ordinals MUST be renumbered so every 1-pager in the directory has a unique ordinal

### Requirement: Documentation Index

`docs/README.md` SHALL exist and list every document under `docs/` with a one-line description of what it covers.

#### Scenario: A document is added, renamed, or removed

- **WHEN** any file under `docs/` is created, renamed, or removed
- **THEN** `docs/README.md` MUST be updated in the same change, so the index never references a missing file and never omits an existing one

### Requirement: Implementation Status Index

`docs/README.md` SHALL carry a status table listing every 1-pager with the count of its stories that are not started, in progress, and implemented. The table MUST be derived from the state of `openspec/specs/` and `openspec/changes/` rather than maintained as an independent record.

#### Scenario: The status table disagrees with the specs

- **WHEN** the status table reports a story as implemented but no requirement in `openspec/specs/` cites that story
- **THEN** the specs are authoritative and the table MUST be corrected to match them

#### Scenario: A change is archived

- **WHEN** a change is archived and its requirements are folded into `openspec/specs/`
- **THEN** the status table MUST be refreshed so the stories that change realized are reported as implemented

### Requirement: Undecided Product Name Placeholder

Until the product name is chosen, documents SHALL refer to the product using the single placeholder token `{{PRODUCT_NAME}}`. No other spelling, working title, or invented name may be used.

#### Scenario: Product name is chosen

- **WHEN** the final product name is selected
- **THEN** every occurrence of `{{PRODUCT_NAME}}` across `docs/` MUST be replaced in one pass, and the index MUST record the chosen name

#### Scenario: An ad-hoc name appears in a document

- **WHEN** a document introduces a working product name instead of the placeholder
- **THEN** it MUST be replaced with `{{PRODUCT_NAME}}`, so a single later substitution remains sufficient

### Requirement: Cross-Document Reference Integrity

Any persona referenced in a 1-pager SHALL be defined in `personas.md`, and any document referenced from the index SHALL exist.

#### Scenario: A 1-pager names an undefined persona

- **WHEN** a functional requirement names a persona that does not appear in `personas.md`
- **THEN** either the persona MUST be added under the persona rules, or the requirement MUST be reassigned to an existing persona

### Requirement: Superseded Versions Are Retained On Composition Change

A document version replaced by a **composition change** SHALL be retained under `docs/drafts/` as `<document>-v<N>.md`, numbered sequentially, and MUST NOT be deleted or overwritten. A composition change is one that alters what the document asserts or which items it contains: rewording the vision statement, adding or removing a persona, rewriting a problem statement, or withdrawing or replacing a story.

Additive and corrective edits SHALL NOT produce a retained version. Appending a story, adding an assumption, tightening a non-functional requirement, correcting a factual detail, and fixing wording or typography are ordinary edits, and git history is the record for them.

#### Scenario: A document's composition changes

- **WHEN** a persona is added or removed, the vision statement is reworded, a problem statement is rewritten, or a story is withdrawn or replaced
- **THEN** the prior version MUST first be written to the next unused `drafts/<document>-v<N>.md`, with a note of what changed and why, before the current file is updated

#### Scenario: A document is edited additively or corrected

- **WHEN** a story is appended, an assumption is added, a threshold is tightened, or a factual detail is corrected
- **THEN** no version is retained, because retaining one for every such edit buries the composition changes that are worth reading among edits that are not
