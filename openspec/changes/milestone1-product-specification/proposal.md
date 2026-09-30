## Why

Milestone 1 of CS 3365 requires students to explore product definition, personas, and epics without writing application code. However, without explicit documentation standards and quality gates, teams suffer from inconsistent persona formats, vague problem statements, artificial "user goals" rejected by textbook best practices, and unstructured requirements sizing. Furthermore, as products evolve through discovery iterations, teams lack a systematic method to preserve early draft snapshots and capture why decisions changed without digging through noisy Git commit diffs.

This change establishes the formal specification and governance standard for all Milestone 1 documentation. It defines the required anatomy, constraints, and validation criteria for Product Visions, Personas, 1-Pagers, and Requirements Sizing, while establishing a two-tier documentation architecture (`docs/` for canonical deliverables and `docs/drafts/` for evolution tracking) to govern subsequent implementation milestones.

## What Changes

- **Product Vision Standard:** Establishes formal criteria for authoring vision statements, mandating Geoffrey Moore's positioning template, Sommerville's three fundamental product questions, and the three core design trade-off pairs.
- **Persona Definition Standard:** Defines normative requirements for user personas, enforcing Sommerville's four dimensions (Personalization, Job, Education/Tech Skills, Relevance), mandating technical literacy levels to guide UI design, and strictly prohibiting arbitrary "user goals".
- **Epic 1-Pager Standard:** Establishes the exact structure and validation rules for 1-pagers adhering to the `project1.md` template (Sommerville narrative scenario, technical/business assumptions, user stories with details, non-functional metrics, and Fibonacci sizing with written rationales).
- **Documentation Lifecycle & Governance Standard:** Formalizes the two-tier documentation architecture (`docs/` and `docs/drafts/`), defining snapshot policies for substantial architectural pivots vs. minor edits, mandatory change-rationale headers, and pre-implementation consultation rules for developers.

## Capabilities

### New Capabilities
- `product-vision-standard`: Requirements and normative structure for authoring product vision statements, establishing value propositions, addressing market dissatisfaction, and balancing design trade-offs.
- `persona-definition-standard`: Rules and constraints for defining target user personas derived from the product vision, enforcing the four dimensions and prohibiting arbitrary "user goals".
- `epic-1pager-standard`: Template structure, narrative scenario requirements, functional user story syntax, non-functional criteria, and Fibonacci sizing protocols for feature 1-pagers.
- `documentation-lifecycle-standard`: Repository organization rules, draft archival criteria for substantial pivots, evolution critique headers, and code consultation workflows.

### Modified Capabilities
None. This change defines the initial baseline specification for project documentation standards.

## Impact

- **Documentation Organization:** Directs all canonical deliverables to `docs/` and historical snapshots to `docs/drafts/`.
- **Milestone 1 Deliverables:** Governs the authoring and evaluation of `docs/01-product-vision.md`, `docs/02-personas.md`, `docs/03-backlog-and-sizing.md`, and `docs/epics/*.md`.
- **Milestone 2 Coding Transition:** Establishes the authoritative acceptance criteria and consultation protocol that developers and AI agents must follow before implementing code in subsequent project phases.
