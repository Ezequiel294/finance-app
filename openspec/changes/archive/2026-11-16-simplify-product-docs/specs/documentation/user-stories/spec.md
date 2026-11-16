## REMOVED Requirements

### Requirement: Story Format

**Reason**: Stories no longer name a persona. Instead, each story states the situation that made the persona relevant.
**Migration**: See **Story Format** in `documentation/epics` ("When…, I want to…, so that…"). All existing stories are rewritten.

### Requirement: Stories Name A Defined Persona

**Reason**: Personas are removed.
**Migration**: None. The "When" part of each story takes the persona's place.

### Requirement: Stories Describe One Thing

**Reason**: Moves, with the other story rules, into one spec.
**Migration**: Kept as **Stories Describe One Thing** in `documentation/epics`.

### Requirement: Supporting Detail Bullets

**Reason**: Detail bullets are now needed only when a story is pulled, not when it is first written.
**Migration**: See **Detail Bullets Are Added When A Story Is Pulled** in `documentation/epics`.

### Requirement: Epics Are Recognised And Split Before Implementation

**Reason**: Splitting was triggered by a story-point limit, and story points are removed. Also, "epic" now means the file that groups stories, not a story that is too big.
**Migration**: See **Oversized Stories Are Split** in `documentation/epics`. A story is split when it won't fit in one change.

### Requirement: Negative Stories Are Reframed

**Reason**: Merged with the rule about naming mechanisms into one requirement.
**Migration**: See **Stories Are Positive And Name No Mechanism** in `documentation/epics`.

### Requirement: Stories Avoid Implementation Prescription

**Reason**: Merged with the rule about negative stories into one requirement.
**Migration**: See **Stories Are Positive And Name No Mechanism** in `documentation/epics`.

### Requirement: Stable Story Identifiers

**Reason**: Moves, with the other story rules, into one spec.
**Migration**: Kept as **Stable Story Identifiers** in `documentation/epics`. No existing ID changes.

### Requirement: Stories Are Durable

**Reason**: Merged with the rule about withdrawn stories into one requirement.
**Migration**: See **Stories Are Never Deleted** in `documentation/epics`.

### Requirement: Implementation Status Is Derived From Specs

**Reason**: Moves into the epics spec. The status table it used to feed is removed.
**Migration**: Kept as **Implementation Status Is Derived From Specs** in `documentation/epics`, which now also forbids a saved status table.

### Requirement: Specs Cite The Stories They Realize

**Reason**: It repeats the citation rule in `process/capability-layout`. Also, under `process/vertical-slices` every product change realizes exactly one story, so every product requirement already has one.
**Migration**: The `Realizes:` rule in **A Capability Describes Behavior, Not A Story** (`process/capability-layout`) applies.

### Requirement: Withdrawn Stories Are Marked, Not Deleted

**Reason**: Merged with the rule that stories are durable into one requirement.
**Migration**: See **Stories Are Never Deleted** in `documentation/epics`.
