## Context

See `proposal.md` for overall motivation. Milestone 1 of CS 3365 focuses strictly on requirements engineering, product vision, persona definitions, and feature 1-pagers without writing software code. The architectural challenge of this milestone is establishing a rigorous documentation framework that satisfies class grading rubrics, prevents documentation rot, and provides a clear contract that software engineers can consult when implementation begins in Milestone 2.

## Goals / Non-Goals

**Goals:**
- Provide a standardized, enforceable documentation schema for Product Visions, Personas, 1-Pagers, and Requirements Sizing.
- Establish a two-tier documentation architecture: clean, printable canonical Markdown in `docs/` and historical snapshots in `docs/drafts/`.
- Capture the AI PM simulation evolution and prompt critique required by `project1.md` without polluting the git log.
- Define the pre-implementation consultation protocol for developers in Milestone 2.

**Non-Goals:**
- Authoring application source code, mobile views, or backend services during Milestone 1.
- Creating native bridging modules or database migration scripts prior to Milestone 2 kickoff.

## Decisions

### 1. Two-Tier Documentation Architecture (`docs/` vs. `openspec/`)
- **Choice:** Canonical product deliverables reside in `docs/` (`01-product-vision.md`, `02-personas.md`, `03-backlog-and-sizing.md`, and `epics/`), while OpenSpec functions as the governing rules and verification engine.
- **Rationale:** Keeps deliverables human-readable, easily printable for physical submission on October 1, and organized like a professional open-source project, while OpenSpec prevents requirement drift.
- **Alternatives Considered:**
  - *Keeping all documents inside `openspec/changes/...`:* Obscures documentation from teammates and instructors who want to read clean Markdown files in the repository root.

### 2. Selective Draft Snapshotting Policy (`docs/drafts/`)
- **Choice:** Snapshot earlier versions into `docs/drafts/<document>-v[N].md` only when a substantial architectural or requirement pivot occurs, prepending a mandatory "Evolution & Why This Changed" critique header. Minor typos and formatting edits are applied directly to canonical files.
- **Rationale:** Directly satisfies the `project1.md` rubric requirement for "early draft versions and critique of different models" while preventing `docs/drafts/` from becoming cluttered with trivial git-level diffs.
- **Alternatives Considered:**
  - *Snapshotting on every edit:* Creates hundreds of redundant files, making the drafts folder as tedious to navigate as git log.
  - *Relying solely on Git commits:* Inaccessible during physical paper grading and difficult for non-technical stakeholders to evaluate.

### 3. Pre-Implementation Consultation Protocol for Milestone 2
- **Choice:** When coding begins in Milestone 2, each implementation task must explicitly cite and verify acceptance criteria from its corresponding epic in `docs/epics/`.
- **Rationale:** Ensures complete traceability from user stories to pull requests, preventing feature creep and unvalidated assumptions.

## Risks / Trade-offs

- **[Risk: Team members write inconsistent personas or invent arbitrary "user goals"]**  
  → *Mitigation:* `openspec/config.yaml` and `specs/persona-definition-standard/spec.md` establish automated quality gates enforcing Sommerville's 4 dimensions and prohibiting goals.
- **[Risk: Drafts directory accumulates trivial noise]**  
  → *Mitigation:* The selective snapshot policy defines explicit criteria for what constitutes a "substantial change" (e.g., changing banking ecosystem, substituting a primary persona, or adding fee formulas).
