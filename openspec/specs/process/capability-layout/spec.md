# process/capability-layout Specification

## Purpose
Defines where product capability specs live and what a capability is, so that the current behavior of any area of the product can be read in one place, and defines where the structure of the implementation is documented.

## Requirements

### Requirement: Product Specs Are Organized By Epic And Capability

Each product capability spec SHALL live at `openspec/specs/<epic-slug>/<capability>/spec.md`, where `<epic-slug>` is the file name of the 1-pager whose story introduced the capability, without its ordinal prefix or extension, and `<capability>` is a kebab-case name for an area of behavior.

#### Scenario: A product spec is created outside an epic folder

- **WHEN** a product capability spec is created directly under `openspec/specs/` or under a folder that is not an epic slug
- **THEN** it MUST be moved under the epic slug of the 1-pager that introduced it

#### Scenario: 1-pager ordinals are renumbered

- **WHEN** 1-pagers are renumbered under the documentation rules
- **THEN** no product spec path changes, because the epic slug excludes the ordinal

### Requirement: A Capability Describes Behavior, Not A Story

A capability SHALL describe one area of the product's behavior as it currently stands. Several stories MAY add to or modify the same capability. Each requirement in a product capability spec SHALL cite every story it realizes on a line of the form `Realizes: <NN>-S<NN>`, listing several identifiers separated by commas where more than one story shaped it.

#### Scenario: A story changes behavior an existing capability describes

- **WHEN** a story alters behavior already specified in an existing capability
- **THEN** its change MUST modify the requirement in that capability and add its story identifier to the requirement's citation, rather than creating a new capability, so the current behavior is never split across places

#### Scenario: A capability is named after a story

- **WHEN** a capability's name is a story identifier or restates a single story's task
- **THEN** it MUST be renamed for the area of behavior it describes

### Requirement: A Capability Lives Where It First Appears

A capability SHALL remain under the epic slug where it was first created. A story from a later epic that changes it SHALL modify it at that path. The same area of behavior MUST NOT be specified by more than one capability.

#### Scenario: A later epic's story extends an existing capability

- **WHEN** a story from one epic changes behavior specified by a capability under another epic's folder
- **THEN** its delta spec MUST target the existing capability's path, and MUST NOT create a parallel capability under its own epic

### Requirement: Behavior In Specs, Structure In The Architecture Document

Product capability specs SHALL describe observable behavior only. The structure of the implementation — its stack, layers, module layout, data storage, and the decisions behind them — SHALL be described in `docs/architecture.md`, which is created by the first product change and updated by every change whose design makes a structural decision, each decision linking to the archived change that made it.

#### Scenario: A change makes a structural decision

- **WHEN** a change's `design.md` introduces or alters the stack, a layer boundary, the module layout, or how data is stored
- **THEN** `docs/architecture.md` MUST be updated in the same change, because a decision that exists only in an archived design is effectively lost to anyone joining later

#### Scenario: A spec names an implementation detail

- **WHEN** a product capability spec names a framework, library, module, or table
- **THEN** that detail MUST be moved to `docs/architecture.md` or the change's `design.md`, leaving only the observable behavior in the spec
