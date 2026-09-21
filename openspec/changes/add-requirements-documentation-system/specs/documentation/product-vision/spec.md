## Purpose

Defines how a product vision statement is written, retained across drafts, and used as the reference against which every proposed product feature is checked.

## ADDED Requirements

### Requirement: Vision Template Structure

The product vision SHALL be expressed using Moore's template and MUST contain all six clauses in order: **FOR** (target customer), **WHO** (statement of the need or opportunity), **THE** `<product name>` **is a** `<product category>`, **THAT** (key benefit, compelling reason to buy), **UNLIKE** (primary competitive alternative), **OUR PRODUCT** (statement of primary differentiation).

#### Scenario: A clause is missing

- **WHEN** a vision statement omits any of the six clauses
- **THEN** it is incomplete and MUST be revised before personas are derived from it

#### Scenario: The UNLIKE clause names no real alternative

- **WHEN** the UNLIKE clause describes a generic category rather than an identifiable competing product or the user's current way of working
- **THEN** it MUST be rewritten to name the actual alternative the product displaces

### Requirement: Vision Answers Three Questions

The vision SHALL answer, without requiring any other document: what the product is and what makes it different from competing products; who the target users and customers are; and why customers would choose it.

#### Scenario: Vision is reviewed for completeness

- **WHEN** a reader who has seen no other project document reads only the vision
- **THEN** they MUST be able to state the product's what, who, and why

### Requirement: Vision Length And Tone

The vision SHALL be a succinct statement, not a specification. It MUST NOT enumerate features, screens, data models, or implementation technologies.

#### Scenario: Vision drifts into a feature list

- **WHEN** a vision statement enumerates specific product features or technical components
- **THEN** those details MUST be removed from the vision and carried instead into the 1-pagers that cover them

### Requirement: Draft Retention

Every superseded version of the vision SHALL be retained at `docs/<product-slug>/drafts/vision-v<N>.md`, numbered sequentially from 1, and MUST NOT be deleted or overwritten. `vision.md` always holds the current version.

#### Scenario: The vision is revised

- **WHEN** the vision is changed for any reason
- **THEN** the prior text MUST first be written to the next unused `drafts/vision-v<N>.md` before `vision.md` is updated

#### Scenario: A draft records no reason for the change

- **WHEN** a retained draft is stored without a note of what changed and why
- **THEN** that note MUST be added, since the evolution of the vision is itself graded evidence

### Requirement: Vision Governs Feature Inclusion

Every feature proposed in a 1-pager SHALL be checkable against the vision. A feature that the vision does not support MUST either be rejected or trigger an explicit, drafted revision of the vision.

#### Scenario: A proposed feature falls outside the vision

- **WHEN** a functional requirement is proposed that the current vision does not support
- **THEN** either the requirement is dropped, or the vision is revised through the draft-retention process and the change is recorded

### Requirement: Placeholder Name In Vision

While the product name is undecided, the **THE** clause SHALL use the `{{PRODUCT_NAME}}` placeholder. The product category in that clause MUST still be stated concretely.

#### Scenario: Vision is written before the name is chosen

- **WHEN** the vision is authored with no product name selected
- **THEN** it MUST read "THE {{PRODUCT_NAME}} is a `<concrete category>`", leaving the category filled in and only the name deferred
