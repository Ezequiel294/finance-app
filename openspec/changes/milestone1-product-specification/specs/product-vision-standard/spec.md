## Purpose

Defines the normative structure, required elements, and quality criteria for authoring product vision statements for CS 3365 software products.

## ADDED Requirements

### Requirement: Moore's Vision Template Compliance
The product vision statement SHALL follow Geoffrey Moore's keyword-structured template from *Crossing the Chasm* as referenced in Ian Sommerville's *Engineering Software Products* (Chapter 1, Section 7).

#### Scenario: Full Moore keyword template verification
- **WHEN** the product vision statement is evaluated
- **THEN** it contains explicit clauses for `FOR` (target customer), `WHO` (statement of need/opportunity), `THE` (product name and category), `THAT` (key benefit/compelling reason to buy), `UNLIKE` (primary competitive alternative), and `OUR PRODUCT` (statement of primary differentiation)

### Requirement: Answering the Three Fundamental Questions
The product vision documentation SHALL explicitly answer Ian Sommerville's three fundamental product questions to establish commercial and operational viability.

#### Scenario: Three questions validation
- **WHEN** reviewing the vision documentation
- **THEN** it explicitly answers: (1) What is the product and what makes it distinct from existing alternatives, (2) Who are the target users and customers, and (3) Why should customers choose or buy this product

### Requirement: Explicit Design Trade-Off Alignment
The product vision SHALL declare the product's strategic positioning across Sommerville's three fundamental trade-off pairs (Chapter 3, Section 6).

#### Scenario: Evaluation of design trade-offs
- **WHEN** assessing the product's architectural scope
- **THEN** the documentation explicitly articulates the balance chosen between: (1) Simplicity vs. Functionality, (2) Familiarity vs. Novelty, and (3) Automation vs. Control
