## Purpose

Defines the normative structure, dimensional constraints, and authoring guidelines for target user personas derived from product vision statements.

## ADDED Requirements

### Requirement: Mandatory Four-Dimension Persona Structure
Each persona definition SHALL be structured as a character portrait covering all four dimensions defined in Sommerville's *Engineering Software Products* (Chapter 3, Section 3).

#### Scenario: Persona dimension completeness
- **WHEN** any persona definition is inspected
- **THEN** it explicitly contains: (1) Personalization (name, age, living circumstances), (2) Job-related context (employment dynamics, work routine), (3) Education and technical literacy, and (4) Relevance (why the product matters and how they intend to use it)

### Requirement: Strict Rejection of User Goals
Persona definitions SHALL NOT include standalone "user goals" sections, adhering to Sommerville's principle that goals are impossible to pin down and unhelpful for software engineers.

#### Scenario: Verification of user goals omission
- **WHEN** auditing persona definitions for methodological compliance
- **THEN** no standalone "Goals", "Aspirations", or "Objectives" sections exist, and user motivation is expressed strictly through concrete use cases within the Relevance dimension

### Requirement: Persona Cohort Quantity and Diversity
The set of personas created for a product SHALL contain between three and five distinct archetypes to avoid design overlap while ensuring comprehensive coverage.

#### Scenario: Persona cohort bounds check
- **WHEN** validating the persona suite for a product deliverable
- **THEN** the total count of defined personas is between 3 and 5, and each persona represents a distinct financial user archetype (e.g., student/multi-currency builder, corporate executive investor, privacy-focused power user)

### Requirement: Technical Literacy as an Interface Design Constraint
The education and technical skills dimension of each persona SHALL explicitly articulate the user's level of technical literacy to establish constraints for user interface complexity.

#### Scenario: Interface constraint derivation
- **WHEN** designers and developers review a persona
- **THEN** the persona's technical literacy indicates whether the user requires guided progressive disclosure (e.g., beginner) or demands high-density, shortcut-driven power interfaces (e.g., systems engineer)
