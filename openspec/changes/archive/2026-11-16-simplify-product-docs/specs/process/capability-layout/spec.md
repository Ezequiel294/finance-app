## ADDED Requirements

### Requirement: Product Specs Are Organized By Epic Slug And Capability

Each product spec SHALL live at `openspec/specs/<epic-slug>/<capability>/spec.md`.
- `<epic-slug>` is the file name of the epic in `docs/epics/` whose story created the capability, without its number or file extension. For example, `01-accounts-and-transaction-ingestion.md` gives `accounts-and-transaction-ingestion`.
- `<capability>` is a kebab-case name for one area of behavior.

#### Scenario: A product spec is created outside an epic folder

- **WHEN** a product spec is created directly under `openspec/specs/`, or under a folder that isn't an epic slug
- **THEN** it MUST be moved under the slug of the epic that created it

#### Scenario: Epic ordinals are renumbered

- **WHEN** epics are renumbered under the documentation rules
- **THEN** no product spec moves, because the epic slug doesn't include the number

## REMOVED Requirements

### Requirement: Product Specs Are Organized By Epic And Capability

**Reason**: It took the epic slug from a 1-pager, and 1-pagers become epics in `docs/epics/`.
**Migration**: See **Product Specs Are Organized By Epic Slug And Capability**. The path rule is the same, but the slug now comes from the epic file.
