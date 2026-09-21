## Purpose

Defines the required structure of a 1-pager, what belongs in each of its sections, and what makes its PROBLEM section a properly written narrative scenario rather than a specification.

## ADDED Requirements

### Requirement: Required Section Structure

Each 1-pager SHALL contain exactly these five sections, with these headings, in this order: **PROBLEM**, **ASSUMPTIONS**, **FUNCTIONAL REQUIREMENTS**, **NON-FUNCTIONAL REQUIREMENTS**, **REQUIREMENTS SIZING**. The document MUST open with a title naming the initiative.

#### Scenario: A section is missing, renamed, or reordered

- **WHEN** a 1-pager omits a required section, uses a different heading, or reorders them
- **THEN** it MUST be corrected to match the template exactly, because readers rely on finding the same sections, under the same names, in every 1-pager

#### Scenario: An extra section is introduced

- **WHEN** a 1-pager adds a section not in the template
- **THEN** its content MUST be relocated into one of the five required sections

### Requirement: PROBLEM Is A Narrative Scenario

The PROBLEM section SHALL be one to two paragraphs of continuous prose describing a situation in which a named persona uses the product's features to do something they want to do. It MUST be written from the user's perspective.

#### Scenario: PROBLEM is written as a structured list

- **WHEN** the PROBLEM section uses bullet points, numbered steps, field labels, or WHEN/THEN clauses
- **THEN** it MUST be rewritten as continuous narrative prose, because structured scenarios are harder for non-engineer readers to check

#### Scenario: PROBLEM describes the system instead of the user

- **WHEN** the PROBLEM section describes what the system does rather than what a person is trying to do
- **THEN** it MUST be rewritten from the perspective of a named persona performing an activity

### Requirement: PROBLEM Scenario Elements

The PROBLEM section SHALL contain a brief statement of the overall objective, a reference to at least one persona defined in `personas.md`, information about what is involved in doing the activity, and an explanation of the problem that cannot readily be addressed by the way the persona works today. It MAY describe one way the problem might be addressed.

#### Scenario: The scenario states no unmet problem

- **WHEN** a PROBLEM section describes an activity that the persona's current tools already handle well
- **THEN** it MUST be revised to state what specifically cannot be done today, or the 1-pager MUST be dropped

#### Scenario: The scenario references no persona

- **WHEN** a PROBLEM section describes a generic or unnamed user
- **THEN** it MUST be rewritten to reference a persona by name from `personas.md`

### Requirement: PROBLEM Is Not A Specification

The PROBLEM section SHALL NOT be treated as complete or authoritative. It MUST NOT contain acceptance criteria, data schemas, API definitions, or interface layouts.

#### Scenario: Implementation detail appears in PROBLEM

- **WHEN** a PROBLEM section specifies fields, endpoints, screens, or acceptance criteria
- **THEN** that content MUST move to FUNCTIONAL REQUIREMENTS, NON-FUNCTIONAL REQUIREMENTS, or ASSUMPTIONS as appropriate

### Requirement: Assumptions Are Explicit And Sourced

The ASSUMPTIONS section SHALL record every technical and business assumption relied on by the requirements in that 1-pager. Each assumption MUST be stated as a single checkable claim, and MUST be marked either **verified** with a source and the date it was checked, or **unverified** with what would confirm or refute it.

#### Scenario: An assumption is stated without evidence

- **WHEN** an assumption asserts an external fact — a rate limit, an API capability, a platform restriction — with no source
- **THEN** it MUST be marked unverified and state what investigation would settle it

#### Scenario: A verified assumption is later contradicted

- **WHEN** evidence shows a verified assumption is no longer true
- **THEN** the assumption MUST be updated with the new finding and date, and every requirement that depended on it MUST be re-examined

### Requirement: Non-Functional Requirements Coverage

The NON-FUNCTIONAL REQUIREMENTS section SHALL address, at minimum, security level, service-level expectations, and performance. Each entry MUST state a measurable threshold or a named standard rather than an adjective.

#### Scenario: A non-functional requirement is unmeasurable

- **WHEN** an entry says the system should be "fast", "secure", or "reliable" without a threshold or named standard
- **THEN** it MUST be restated with a number, a named standard, or an explicit stated target

### Requirement: One-Pager Scope

Each 1-pager SHALL cover one coherent initiative — a single epic's worth of functionality — and its functional requirements MUST all serve the situation described in its PROBLEM section.

#### Scenario: A 1-pager covers unrelated initiatives

- **WHEN** a 1-pager's functional requirements serve situations its PROBLEM section does not describe
- **THEN** it MUST be split into separate 1-pagers, each with its own PROBLEM

### Requirement: Persona Coverage Across One-Pagers

Every persona defined in `personas.md` SHALL appear as the subject of at least one functional requirement in at least one 1-pager.

#### Scenario: A persona appears in no 1-pager

- **WHEN** a defined persona is the subject of no functional requirement anywhere
- **THEN** either a 1-pager MUST cover that persona's needs, or the persona MUST be removed from the set
