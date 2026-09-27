## Context

See `proposal.md` — Why. The constraints that shape this design:

- `openspec/specs/` is currently empty, so this change sets the project's spec organization convention.
- The documents describe a product intended to be built and used, not a one-off deliverable. They must stay useful to someone reading them long after they were written.
- The product name is not yet chosen, and must be deferrable without invalidating documents written now.
- The team has no issue tracker or board. Whatever answers "what is built and what is not" has to come from the repository itself.
- The 1-pager structure and the requirements practice follow Sommerville, *Engineering Software Products*, Chapter 3.

## Goals / Non-Goals

**Goals:**

- Make the authoring conventions for each document type checkable, so a document can be verified against its rule rather than against remembered house style.
- Keep the conventions durable and the content separate, so the rules survive the archival of this change.
- Use one mechanism for documentation now and product capabilities later, so development adds capabilities beside these rather than replacing them.
- Make implementation status derivable from the repository, so the project needs no external tracker and no record that can silently fall out of date.

**Non-Goals:**

- Writing the document content. That is this change's implementation output.
- Specifying the product itself. Its capabilities are separate changes taken up when development begins.
- Automated enforcement. These specs are read and applied by people and tools; no linter is built.
- Prescribing who or what authors a document. The rules constrain the result, not the means of producing it.

## Decisions

### Use the stock `spec-driven` schema rather than a custom one

The alternative was `openspec schema fork spec-driven` with artifacts named `vision`, `personas`, `one-pagers`, and `sizing`. This was investigated before being rejected:

- `openspec schema init --artifacts "vision,personas,..."` is refused outright: `{"error": "Unknown artifact 'vision'", "valid": ["proposal","specs","design","tasks"]}`.
- Forking and hand-editing `schema.yaml` with custom artifact IDs does validate and run end to end, but every schema command prints *"Schema commands are experimental and may change."*

Beyond the stability concern, the fork approach conflates two different things. It would make each document type an *artifact of a change*, when what is durable is the *rule* for writing that document type. The stock schema expresses this correctly: the rules are specs, the documents are the change's output.

### Specs govern documents; `docs/` holds document content

`openspec/changes/` is temporary and is archived once a change completes; `openspec/specs/` is permanent and is what every later change consults. Document content therefore cannot live in the change directory, or it disappears from the working set when this change is archived. The split is: `openspec/specs/documentation/**` holds how to write, read, and update each document type; `docs/**` holds the documents themselves.

A consequence worth stating plainly: for this change, the documentation *is* the implementation. Apply produces Markdown under `docs/`, not code.

### Six capabilities, namespaced under `documentation/`

The alternative was fewer capabilities, folding `user-stories` and `requirements-sizing` into `one-pagers` as sections of that template. They were kept separate because both are used outside 1-pagers — stories become the unit of work during development, and sizing drives what a team commits to — and a capability others depend on should not be a subsection of one of them.

The `documentation/` path segment namespaces these away from the product capabilities added later, so `openspec/specs/` does not become a flat mix of process rules and product behavior.

### Implementation status is derived, not tracked

With no board, the obvious move is a status marker on each story. It was rejected: a hand-maintained marker is a second record of a fact the repository already knows, and two records of the same fact diverge. The first time someone implements a story and forgets to tick it, the document starts lying, and thereafter nobody trusts it.

Instead the repository *is* the tracker. `openspec/specs/` describes what the system does, so a story cited by a requirement there is built. `openspec/changes/` holds work in flight, so a story cited only by an active change is in progress. A story cited by neither has not been started. `openspec list` shows what is currently in flight.

The citation runs from spec to story, not story to spec. That direction was chosen so that 1-pagers stay stable: the link is written while editing the spec, which is already being edited, rather than requiring an edit to a requirements document every time something ships. Stories therefore need stable identifiers that survive reordering, which is why identifiers are assigned once and never reused.

### Implemented stories stay in their 1-pager

The alternative considered was deleting a story once built, leaving the 1-pager as a list of outstanding work and relying on git history to recover what was once there.

It was rejected. A 1-pager is a standing description of an initiative: a problem statement and the set of requirements that answer it. Strip the built stories and a mature initiative reads as though almost nothing about it is needed, which is actively misleading to a new reader. Git history is also a poor place to look for intent — nobody reconstructs requirements by walking commits, and a story recoverable only by archaeology is not documentation.

So stories are durable, and a story that will never be built is marked withdrawn with its reason rather than removed, because the absence of a capability is itself something a later reader will ask about.

### Narrative scenarios and spec scenarios are kept distinct

Two different things are called a "scenario" here, and conflating them would damage both:

| | Narrative scenario | OpenSpec `#### Scenario:` |
|---|---|---|
| Form | Prose, one to two paragraphs | Structured **WHEN** / **THEN** |
| Lives in | A 1-pager's PROBLEM section | `specs/**/spec.md` |
| Purpose | Convey a person's situation; provoke thinking | Testable behavior contract |

The `one-pagers` capability therefore requires PROBLEM to be continuous prose and forbids WHEN/THEN there — even though the spec stating that rule is itself written in WHEN/THEN. Structured scenarios read as intimidating to the non-engineer readers who are best placed to check whether a scenario is true to life, which is exactly why the narrative form is required for that section.

### Markdown in git rather than a requirements tool

Git supplies what a wiki would not: every revision is attributable and dated, superseded versions are retained deliberately rather than buried in page history, and the documents travel with the code that implements them. The cost is that nothing enforces the rules automatically, which the compliance review in the task breakdown accepts explicitly.

## Risks / Trade-offs

- **Process rules become bureaucratic and slow the work** → Every requirement here traces to a named constraint from Sommerville Ch3 or to a failure mode these documents are known to fall into. A rule that traces to neither should be removed rather than followed.

- **Six documentation capabilities crowd out product capabilities later** → The `documentation/` namespace keeps them separable, and they are stable once written; they are read far more often than edited.

- **Derived status is only as good as the citations** → If a requirement omits the story identifier it realizes, that story reads as unstarted. The `user-stories` capability makes citation mandatory, and the status table is defined as derived so a disagreement is resolved in favour of the specs rather than papered over.

- **Specs are enforced by reading, not tooling** → `openspec validate` checks structure, not whether a document complies with its rule. Compliance is a review step, which the task breakdown makes explicit rather than implicit.

- **The documentation rules could ossify** → These specs are themselves changeable through the normal change workflow. If a rule proves wrong in practice, the correct response is a change that amends it, not a document that quietly ignores it.

## Open Questions

Deferrable without changing the specs, the approach, or the task breakdown:

- **The product name.** The `doc-structure` capability mandates the `{{PRODUCT_NAME}}` placeholder and a single substitution pass, so the name can be chosen at any point.
