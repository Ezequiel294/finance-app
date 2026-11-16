## Purpose

Defines how epics are named and laid out, how stories are written, numbered, split, and kept, how to tell which stories are built, and where a new idea should go.

## ADDED Requirements

### Requirement: Epic File Layout

Each epic SHALL be one file at `docs/epics/<NN>-<epic-slug>.md`.
- `<NN>` is a two-digit number, such as `01`. It sets the reading order.
- `<epic-slug>` is the epic's name in kebab-case.

The file SHALL start with a title naming the initiative. It SHALL then have exactly these sections, in this order: **PROBLEM**, **ASSUMPTIONS**, **STORIES**, **NON-FUNCTIONAL REQUIREMENTS**.

#### Scenario: A section is missing, renamed, or reordered

- **WHEN** an epic is missing a section, renames one, adds one, or puts them in a different order
- **THEN** it MUST be fixed to match the layout, because readers expect the same sections in every epic

#### Scenario: Two epics claim the same ordinal

- **WHEN** a new epic uses a number another epic already has
- **THEN** the epics MUST be renumbered so each number is used once

### Requirement: One Problem Per Epic

Each epic SHALL address one problem. Every story in it MUST serve the situations its PROBLEM section describes.

#### Scenario: An epic's stories serve an undescribed situation

- **WHEN** some stories in an epic serve a situation its PROBLEM section doesn't describe
- **THEN** the PROBLEM section MUST be extended to describe it, or those stories MUST move to an epic whose problem they serve

### Requirement: PROBLEM Describes Situations

The PROBLEM section SHALL be one or two paragraphs of plain prose. It SHALL describe:
- the situations people are in;
- what they are trying to do;
- why the way they handle it today doesn't work.

It MUST NOT name individual people or characters. It MUST NOT contain acceptance criteria, data schemas, API definitions, or screen layouts.

#### Scenario: PROBLEM tells a named character's story

- **WHEN** a PROBLEM section describes a named person
- **THEN** it MUST be rewritten to describe the situation that person stood for, such as "holding money at several banks" or "being paid irregularly"

#### Scenario: PROBLEM states no unmet need

- **WHEN** a PROBLEM section describes something people's current tools already handle well
- **THEN** it MUST be changed to say what people can't do today, or the epic MUST be dropped

#### Scenario: Specification detail appears in PROBLEM

- **WHEN** a PROBLEM section lists fields, endpoints, screens, or acceptance criteria
- **THEN** that content MUST move to STORIES, NON-FUNCTIONAL REQUIREMENTS, or ASSUMPTIONS, wherever it fits

### Requirement: Assumptions Are Explicit And Sourced

The ASSUMPTIONS section SHALL list every technical and business assumption the epic's stories depend on. Each assumption MUST be one claim that someone can check. Each MUST be marked as either:
- **verified**, with a source and the date it was checked; or
- **unverified**, with what would prove it true or false.

#### Scenario: An assumption is stated without evidence

- **WHEN** an assumption states an outside fact, such as a rate limit, an API feature, or a platform restriction, without a source
- **THEN** it MUST be marked unverified, and it MUST say what investigation would settle it

#### Scenario: A verified assumption is later contradicted

- **WHEN** new evidence shows a verified assumption is no longer true
- **THEN** the assumption MUST be updated with the new finding and its date, and every story that depended on it MUST be checked again

### Requirement: Non-Functional Requirements Are Measurable

The NON-FUNCTIONAL REQUIREMENTS section SHALL cover at least security, service levels, and performance. Each entry MUST give a measurable threshold or a named standard, not an adjective.

#### Scenario: A non-functional requirement is unmeasurable

- **WHEN** an entry says the product should be "fast", "secure", or "reliable" without a number or a named standard
- **THEN** it MUST be rewritten with a number, a named standard, or a clear target

### Requirement: Story Format

Every story SHALL be written in the first person, in this form:

**When** `<situation>`, **I want to** `<task>`, **so that** `<outcome>`.

The situation SHALL describe the circumstances the person is in. It SHALL NOT describe who they are.

#### Scenario: A story names a person or a role

- **WHEN** a story starts with a named person, or with a role such as "As a user" or "As a freelancer"
- **THEN** it MUST be rewritten to start with the situation that makes the task worth doing

#### Scenario: A story is written as a system statement

- **WHEN** a story is written as "The system shall…" or as just a feature name
- **THEN** it MUST be rewritten in the "When…, I want to…, so that…" form

#### Scenario: The outcome clause is omitted

- **WHEN** a story has a situation and a task but no "so that" part
- **THEN** the "so that" part MUST be added, because the outcome is how a reader judges whether the task is the right fix

### Requirement: Stories Describe One Thing

Each story SHALL ask for one thing from the product.

#### Scenario: A story contains multiple wants

- **WHEN** a story joins several different features with "and" or with a list
- **THEN** it MUST be split into one story per feature

### Requirement: Stories Are Positive And Name No Mechanism

A story SHALL say what the person wants to do, as something they control. It SHALL NOT be phrased as something they don't want. A story SHALL NOT say how the product builds it. Naming a specific technology is allowed only when the person truly needs that technology.

#### Scenario: A need is expressed as a negative

- **WHEN** a story says what the person doesn't want the product to do
- **THEN** it MUST be rewritten as the control the person wants, such as "control and revoke what the product can access", so that a test can show it working

#### Scenario: A story names a mechanism

- **WHEN** a story names a particular technology, library, or interface element
- **THEN** someone MUST check whether the person needs that exact thing or a more general outcome, and if it's the general outcome, the story MUST say that instead

### Requirement: Detail Bullets Are Added When A Story Is Pulled

A story MAY be a single line at first. It stays that way until it is **pulled**: added to `docs/backlog.md` or proposed as a change, whichever happens first.

When a story is pulled, detail bullets SHALL be written under it. They add the detail a change needs. Detail bullets SHALL only explain their own story. They MUST NOT add a feature the story doesn't mention.

#### Scenario: A one-line story is pulled

- **WHEN** a story with no detail bullets is added to the backlog or proposed as a change
- **THEN** its detail bullets MUST be written in its epic in the same edit

#### Scenario: A detail bullet introduces new functionality

- **WHEN** a detail bullet describes a feature its story doesn't mention
- **THEN** that feature MUST become a story of its own

### Requirement: Oversized Stories Are Split

A story that can't be delivered by one change SHALL be split, before it is pulled, into stories that each can. The original story SHALL stay in its epic. It SHALL be marked as replaced, with the IDs of the stories that replace it.

No size estimate is recorded. Whether a story fits in one change is a judgement call, made when the story is written or pulled.

#### Scenario: A story is judged too large for one change

- **WHEN** someone judges that a story is too big for one change
- **THEN** it MUST be split into stories that each cover one aspect, using the next free IDs in its epic, and the original MUST be marked "Replaced by" those IDs

### Requirement: Stable Story Identifiers

Every story SHALL have an ID of the form `<epic number>-S<NN>`, such as `01-S03`. Each ID SHALL be unique across the product and given out once. An ID MUST NOT be reused, renumbered, or moved to a different story.

#### Scenario: Stories are reordered within an epic

- **WHEN** stories in an epic are reordered, inserted, or removed
- **THEN** existing stories MUST keep their IDs, and new stories MUST take the next free number, because specs and changes refer to stories by ID

### Requirement: Stories Are Never Deleted

A story SHALL NOT be deleted from its epic. This holds whether it is built, replaced, or withdrawn. A story the team decides against SHALL be marked withdrawn, with the reason and the date.

#### Scenario: A story is implemented

- **WHEN** a story has been built
- **THEN** it MUST stay in its epic, so the epic still shows everything the product does for that problem

#### Scenario: A story is dropped from scope

- **WHEN** the team decides not to build a story
- **THEN** it MUST be marked withdrawn, with the reason and the date, so anyone who later asks why that feature is missing can find the decision

#### Scenario: A withdrawn story is reinstated

- **WHEN** a withdrawn story is brought back
- **THEN** its withdrawal note MUST be replaced with a note saying it was brought back and when, and the story keeps its original ID

### Requirement: Implementation Status Is Derived From Specs

A story's status SHALL come only from the product specs. Product specs are every spec in `openspec/specs/` and `openspec/changes/` outside the `documentation/` and `process/` folders. Status MUST NOT be written on the story or kept in a table.

A story is:
- **implemented** when a requirement in a product spec under `openspec/specs/` cites its ID;
- **in progress** when the only product requirements citing it are in an active change;
- **not started** when no product requirement cites it.

#### Scenario: Someone asks what remains to be built

- **WHEN** someone needs to know which stories are implemented, in progress, or not started
- **THEN** the answer MUST come from the `Realizes:` lines in the product specs and active changes at that moment, not from any saved copy

#### Scenario: A stored status record appears

- **WHEN** someone writes a status marker on a story, or adds a status table to a document
- **THEN** it MUST be removed, not corrected, because a second record of the same fact will drift away from the specs

#### Scenario: A process or documentation spec mentions a story identifier

- **WHEN** a requirement under `documentation/` or `process/` mentions a story ID, for example as an example
- **THEN** that mention MUST NOT change the story's status, because those folders describe how the product is documented and built, not what it does

### Requirement: New Work Is Routed By Fit

Before anything is written, an exploration of a new idea SHALL decide where the idea belongs. It SHALL ask these questions in order:
1. Does the vision support it?
2. Is it part of a story that isn't built yet?
3. Does an existing epic's PROBLEM cover it?

The answer SHALL depend on fit, not size. Size only decides how many stories an idea becomes, not where they go.

#### Scenario: The vision does not support the idea

- **WHEN** an idea goes against the vision, its principles, or its non-goals
- **THEN** it MUST be dropped, or the vision MUST be deliberately changed before any story is written for it

#### Scenario: The idea falls within a story not yet implemented

- **WHEN** an idea adds detail to what a story already intends, and that story isn't built yet
- **THEN** it MUST be added to that story as a detail bullet, not written as a new story

#### Scenario: The idea extends an implemented story

- **WHEN** an idea adds detail to a story that is already built
- **THEN** it MUST be written as a new story in that story's epic, because changing a built story would make its status wrong

#### Scenario: An existing epic covers the idea

- **WHEN** an existing epic's PROBLEM already describes the situation the idea serves
- **THEN** the idea MUST be written as one or more new stories in that epic, using the next free IDs, no matter how big it is

#### Scenario: The idea needs its own problem

- **WHEN** no existing epic's PROBLEM covers the idea, or the idea needs its own assumptions or non-functional requirements
- **THEN** a new epic MUST be created with the next free number, with its PROBLEM, ASSUMPTIONS, and NON-FUNCTIONAL REQUIREMENTS written in full; its stories MAY each be one line until they are pulled
