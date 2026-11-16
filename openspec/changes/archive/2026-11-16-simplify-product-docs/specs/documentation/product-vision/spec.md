## ADDED Requirements

### Requirement: Vision States Principles And Non-Goals

`docs/vision.md` SHALL contain two sections:
- **Principles**: rules every epic and story must follow across the whole product. Each principle is a claim someone can check.
- **Non-goals**: the user types and features the product deliberately leaves out, each with its reason.

#### Scenario: A story conflicts with a principle

- **WHEN** a story would make the product unusable without a linked account, useless until someone sets it up, or break any other principle
- **THEN** the story MUST be changed to follow the principle, or the principle MUST be deliberately changed first

#### Scenario: A proposed capability matches a non-goal

- **WHEN** an idea serves a user type or feature listed as a non-goal
- **THEN** it MUST be rejected, unless someone first deliberately removes that non-goal and records why

## MODIFIED Requirements

### Requirement: Vision Length And Tone

The vision SHALL be a short statement, not a specification. It MUST NOT list features, screens, data models, or technologies. Principles are rules for the whole product, not features.

#### Scenario: Vision drifts into a feature list

- **WHEN** the vision statement or a principle lists specific features or technical parts
- **THEN** those details MUST be removed from the vision and moved into the epics that cover them

### Requirement: Vision Governs Feature Inclusion

Every epic and story SHALL be checked against the vision, including its principles and non-goals. If the vision doesn't support a story, the story MUST be dropped, or the vision MUST be deliberately changed first.

#### Scenario: A proposed feature falls outside the vision

- **WHEN** someone proposes a story the current vision doesn't support
- **THEN** either the story is dropped, or the vision is changed first, in its own commit whose message says what changed and why

## REMOVED Requirements

### Requirement: Vision Template Structure

**Reason**: Moore's template was a course requirement. The current statement already follows it, but future versions shouldn't be tied to it.
**Migration**: The current vision statement stays as it is. **Vision Answers Three Questions** still requires the vision to say what the product is, who it is for, and why they would choose it.

### Requirement: Draft Retention

**Reason**: Git history already keeps every older version of the vision.
**Migration**: `docs/drafts/vision-v1.md` and `vision-v2.md` are deleted. They can still be recovered from git history. When the vision changes, the commit message says what changed and why.

### Requirement: Placeholder Name In Vision

**Reason**: It repeats the product-wide placeholder rule, and its part about the product category only made sense for Moore's template.
**Migration**: **Undecided Product Name Placeholder** in `documentation/doc-structure` applies to the vision like any other document.
