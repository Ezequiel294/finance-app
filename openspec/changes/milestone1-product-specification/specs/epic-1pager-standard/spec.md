## Purpose

Defines the required sections, narrative scenario rules, user story syntax, non-functional criteria, and sizing protocols for 1-pager epics in accordance with project1.md.

## ADDED Requirements

### Requirement: Strict 1-Pager Template Adherence
Each 1-pager document SHALL strictly follow the five-part template specified at the end of `project1.md`.

#### Scenario: Template section verification
- **WHEN** any epic 1-pager is evaluated
- **THEN** it contains exactly the following five sections in order: `### PROBLEM`, `### ASSUMPTIONS`, `### FUNCTIONAL REQUIREMENTS`, `### NON-FUNCTIONAL REQUIREMENTS`, and `### REQUIREMENTS SIZING`

### Requirement: Problem Statement as Sommerville Narrative Scenario
The `PROBLEM` section of each 1-pager SHALL be written as a one-to-two paragraph narrative scenario matching Sommerville's Chapter 3 guidelines rather than a structured tabular field list.

#### Scenario: Narrative scenario elements check
- **WHEN** reading the `PROBLEM` section
- **THEN** it is composed in natural narrative prose containing: (1) the overall objective, (2) explicit reference to the persona involved, (3) what is involved in the activity, (4) why existing systems fail, and (5) how the proposed capability solves the problem

### Requirement: Assumptions Complementing the Vision
The `ASSUMPTIONS` section SHALL articulate all technical, operational, and business assumptions necessary to ground the feature before implementation.

#### Scenario: Assumptions validation
- **WHEN** reviewing the assumptions of an epic
- **THEN** it explicitly documents constraints such as API rate limits, OS background execution permissions, external exchange feeds, or data caching policies

### Requirement: Functional User Story Syntax and Detail Breakdown
Each functional requirement SHALL follow the standard role-based agile story format and be supplemented with granular implementation details.

#### Scenario: User story format verification
- **WHEN** inspecting functional requirements in a 1-pager
- **THEN** every story matches `* **As a** [persona], **I want to** [perform task] **so that I can/in order to** [benefit]`, followed by bulleted possible details (`* Possible detail A`, `* Possible detail B`)

### Requirement: Measurable Non-Functional Requirements
The `NON-FUNCTIONAL REQUIREMENTS` section SHALL define concrete, verifiable criteria covering security levels, service level agreements (SLAs), and system performance metrics.

#### Scenario: NFR measurability check
- **WHEN** validating non-functional requirements
- **THEN** requirements specify quantifiable metrics such as response times in milliseconds, frame rates in FPS, encryption standards (e.g., AES-256), and availability percentages

### Requirement: Fibonacci Requirements Sizing with Technical Rationale
The `REQUIREMENTS SIZING` section SHALL assign an initial effort estimate using Modified Fibonacci story points (1, 2, 3, 5, 8, 13) and provide a written technical rationale for every story.

#### Scenario: Sizing rationale audit
- **WHEN** reviewing the sizing section of an epic
- **THEN** each functional story is assigned a Fibonacci number and is accompanied by a written explanation justifying the size based on architectural complexity, risk, and development effort
