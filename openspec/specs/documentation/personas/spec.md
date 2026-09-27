## Purpose

Defines how user personas are authored, how many may exist, what each must contain, what they must never contain, and how the persona set is revised when a new persona is proposed.

## Requirements

### Requirement: Persona Count Ceiling

The persona set for a product SHALL contain at most five personas.

#### Scenario: A sixth persona is proposed

- **WHEN** a proposed persona would make the set exceed five
- **THEN** it MUST either be merged into an existing persona or replace one, because overlapping personas make a coherent system harder to design

### Requirement: Each Persona Earns Its Place

Every persona SHALL pull at least one requirement that no other persona in the set pulls.

#### Scenario: A persona duplicates another's requirements

- **WHEN** a proposed persona pulls only requirements already covered by an existing persona
- **THEN** it MUST be merged into that persona rather than added as a separate one

#### Scenario: A persona's distinguishing requirement is removed from scope

- **WHEN** the only requirement a persona uniquely pulls is cut from the product
- **THEN** that persona MUST be re-evaluated for merging or removal

### Requirement: Required Persona Aspects

Each persona SHALL cover four aspects: **personalization** (a name and personal circumstances), **job-related** detail, **education** and level of technical skill and experience, and **relevance** — why this person might be interested in using the product and what they might want to do with it.

#### Scenario: An aspect is missing

- **WHEN** a persona omits any of the four aspects
- **THEN** it MUST be completed before scenarios are written from it

### Requirement: Personas Must Not State Goals

A persona SHALL NOT describe the individual's "goals". Relevance MUST instead be expressed as why the software might be useful to them and examples of what they may want to do with it.

#### Scenario: A persona states goals

- **WHEN** a persona describes the person's goals, objectives, or aspirations
- **THEN** it MUST be rewritten to explain why the product could be useful to them and what they might do with it

### Requirement: Persona Length

Each persona SHALL be two to three paragraphs — short enough to be read and re-read by the whole team.

#### Scenario: A persona exceeds three paragraphs

- **WHEN** a persona grows beyond three paragraphs
- **THEN** it MUST be condensed, keeping the detail that distinguishes it from the other personas

### Requirement: Grounding And Proto-Persona Labelling

Each persona SHALL state what it is based on. A persona derived from observed behaviour or real user data MUST cite that basis. A persona built from limited information MUST be labelled a proto-persona.

#### Scenario: A persona is invented without user research

- **WHEN** a persona is created from team assumptions rather than user data
- **THEN** it MUST be labelled a proto-persona so its lower reliability is visible to every reader

#### Scenario: Real user data is available for a persona

- **WHEN** a persona is grounded in a real user's documented behaviour or artifacts
- **THEN** the persona MUST cite that source, and its details MUST be cross-checked against it rather than invented

### Requirement: Documented Omissions

`personas.md` SHALL contain a section naming the user types deliberately excluded from the set, with the reason for each exclusion.

#### Scenario: A reviewer asks why an obvious user type is absent

- **WHEN** a plausible user type does not appear in the persona set
- **THEN** the omissions section MUST already explain why that type was excluded
