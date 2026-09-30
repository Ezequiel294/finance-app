## Purpose

Defines repository organization, draft versioning rules, change rationale logging, and pre-implementation consultation protocols for product documentation.

## ADDED Requirements

### Requirement: Two-Tier Documentation Directory Hierarchy
The repository SHALL organize product documentation into two distinct tiers: living canonical specifications in `docs/` and historical snapshots in `docs/drafts/`.

#### Scenario: Directory hierarchy verification
- **WHEN** browsing the repository documentation
- **THEN** all current active deliverables reside in `docs/` (`docs/01-product-vision.md`, `docs/02-personas.md`, `docs/03-backlog-and-sizing.md`, and `docs/epics/*.md`), while superseded iterations are archived in `docs/drafts/`

### Requirement: Selective Draft Snapshotting Policy
Draft snapshots SHALL be created in `docs/drafts/` exclusively for substantial architectural or requirement pivots, and SHALL NOT be created for minor typographic, grammatical, or formatting edits.

#### Scenario: Substantial change triggers draft snapshot
- **WHEN** a major requirement evolution occurs (e.g., changing target banking ecosystem, substituting a primary persona, or adding fee formulas)
- **THEN** the previous version is copied to `docs/drafts/<document-name>-v[N].md` before updating the canonical file

#### Scenario: Minor edit bypasses draft snapshot
- **WHEN** a team member fixes a typo, adjusts spacing, or clarifies sentence grammar
- **THEN** the change is applied directly to the canonical file in `docs/` without creating a draft snapshot

### Requirement: Mandatory Evolution Critique Header in Drafts
Every archived draft snapshot in `docs/drafts/` SHALL begin with an "Evolution & Why This Changed" critique section explaining why the version was superseded.

#### Scenario: Draft header compliance audit
- **WHEN** opening any file within `docs/drafts/`
- **THEN** the file opens with standardized metadata (Snapshot Date, Status, Author) followed by three explicit questions: (1) What was deficient in this version, (2) What new insights prompted the change, and (3) What decisions were incorporated into the canonical version

### Requirement: Pre-Implementation Coding Consultation Protocol
Developers and AI agents SHALL consult the canonical 1-pager in `docs/epics/` before authoring application code during subsequent implementation milestones.

#### Scenario: Pre-coding traceability verification
- **WHEN** starting implementation on any user story in Milestone 2
- **THEN** the developer references the functional story details, non-functional latency/security constraints, and assumptions specified in the corresponding `docs/epics/` 1-pager
