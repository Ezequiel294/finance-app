## Purpose

Defines how prompts and AI model outputs are recorded as graded evidence, and how the comparative critique of the models is assembled from document sets that live on separate git branches.

## ADDED Requirements

### Requirement: Every Prompt Is Logged

Every prompt used to generate or revise a Project 1 document SHALL be recorded verbatim in the prompt log, in the order issued.

#### Scenario: A document is generated from an unlogged prompt

- **WHEN** a document is produced or revised by a model using a prompt that was never recorded
- **THEN** that prompt MUST be added to the log before the document is considered complete

#### Scenario: A prompt is paraphrased in the log

- **WHEN** a logged prompt is a summary rather than the exact text issued
- **THEN** it MUST be replaced with the verbatim text, because the wording is what the critique compares

### Requirement: Prompt Log Entry Content

Each log entry SHALL record the verbatim prompt, the model and interface used, the date, and which document or documents the response produced or changed.

#### Scenario: An entry omits the model used

- **WHEN** a log entry does not identify which model answered
- **THEN** the model MUST be recorded, since the critique's conclusions depend on attributing output to a model

### Requirement: Prompt Effectiveness Is Noted

Each log entry SHALL carry a brief note on how well the prompt worked — what the response got right, what it got wrong, and what had to be corrected by hand.

#### Scenario: A prompt required substantial correction

- **WHEN** a model's output had to be significantly rewritten
- **THEN** the entry MUST record what was wrong and what was changed, because this is the evidence the critique draws on

### Requirement: Prompt Log Location

The prompt log SHALL live at `docs/evaluation/prompt-log.md` on the branch whose model it records. Each branch's log MUST cover only that branch's model.

#### Scenario: A prompt log at the repository root

- **WHEN** a prompt log exists outside `docs/evaluation/`
- **THEN** it MUST be relocated to `docs/evaluation/prompt-log.md`

### Requirement: Model Critique Compares Complete Sets

The comparative critique SHALL compare complete document sets produced independently by different models, and MUST NOT be written until both sets exist for the product being compared.

#### Scenario: A critique is attempted from one branch

- **WHEN** a critique is drafted while only one model's document set exists
- **THEN** it MUST be deferred until the other model's set is complete

### Requirement: Critique Content

The critique SHALL state, for each product, which model performed better overall and why, and MUST cite specific passages from the document sets as evidence. It MUST also identify the circumstances under which each model did well and which prompts worked better.

#### Scenario: The critique asserts a winner without evidence

- **WHEN** the critique states one model was better without citing specific passages
- **THEN** the supporting evidence MUST be added, since the rubric grades the justification rather than the verdict

#### Scenario: One model was better only in places

- **WHEN** neither model was better across every artifact type
- **THEN** the critique MUST report that split by artifact type rather than forcing a single overall winner

### Requirement: Critique Assembly Location

Because each model's documents live on its own branch, the critique SHALL be assembled where both sets can be read together, and MUST record which branch and commit each compared document set came from.

#### Scenario: A compared document set is not identified

- **WHEN** the critique quotes a document without recording its branch and commit
- **THEN** that provenance MUST be added, so each claim can be traced to the version it was based on

### Requirement: Human Responsibility For Final Text

Every submitted document SHALL be reviewed and accepted by the team, regardless of which model drafted it. The log records provenance; it does not transfer responsibility for the content.

#### Scenario: Model output is submitted unreviewed

- **WHEN** a document is submitted in the form a model produced it, without team review
- **THEN** it MUST be reviewed and corrected before submission, because the team is accountable for the final text
