## REMOVED Requirements

### Requirement: Required Section Structure

**Reason**: 1-pagers become epics in `docs/epics/`. The REQUIREMENTS SIZING section goes away with story points.
**Migration**: See **Epic File Layout** in `documentation/epics`. The sections are now PROBLEM, ASSUMPTIONS, STORIES, NON-FUNCTIONAL REQUIREMENTS.

### Requirement: PROBLEM Is A Narrative Scenario

**Reason**: The story had to follow a named persona, and personas are removed.
**Migration**: See **PROBLEM Describes Situations** in `documentation/epics`. Existing PROBLEM sections are rewritten as situations.

### Requirement: PROBLEM Scenario Elements

**Reason**: It required a persona. Its other parts are merged into one requirement.
**Migration**: The goal, the activity, and the unmet need are all covered by **PROBLEM Describes Situations** in `documentation/epics`.

### Requirement: PROBLEM Is Not A Specification

**Reason**: Merged into the single PROBLEM requirement in the new spec.
**Migration**: See **PROBLEM Describes Situations** in `documentation/epics`.

### Requirement: Assumptions Are Explicit And Sourced

**Reason**: Moves, with the other epic rules, into one spec.
**Migration**: Kept with the same meaning as **Assumptions Are Explicit And Sourced** in `documentation/epics`.

### Requirement: Non-Functional Requirements Coverage

**Reason**: Moves, with the other epic rules, into one spec.
**Migration**: Kept with the same meaning as **Non-Functional Requirements Are Measurable** in `documentation/epics`.

### Requirement: One-Pager Scope

**Reason**: Moves, with the other epic rules, into one spec.
**Migration**: See **One Problem Per Epic** in `documentation/epics`.

### Requirement: Persona Coverage Across One-Pagers

**Reason**: Personas are removed.
**Migration**: None. The vision, with its principles and non-goals, now says who the product is for.
