## MODIFIED Requirements

### Requirement: Document Set Layout

The product's documentation SHALL occupy `docs/` with this layout: `README.md` (the index), `vision.md`, `personas.md`, `sizing.md`, `backlog.md` (the ordered product backlog), a `one-pagers/` directory, and a `drafts/` directory holding superseded versions. From the first product change onward it SHALL also contain `architecture.md`, describing the structure of the implementation.

#### Scenario: A document is placed outside the defined layout

- **WHEN** a document of one of these types is created at a path the layout does not define
- **THEN** it MUST be moved to its defined path, so every reader finds each document type where it is expected

#### Scenario: The first product change is archived without an architecture document

- **WHEN** the first change that adds a product capability spec is archived and `docs/architecture.md` does not exist
- **THEN** the change is incomplete, and `docs/architecture.md` MUST be written before it is merged
