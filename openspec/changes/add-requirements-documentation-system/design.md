## Context

See `proposal.md` — Why. The constraints that shape this design:

- `openspec/specs/` is currently empty, so this change sets the project's spec organization convention.
- The documents are graded against a fixed external template and rubric in `project1.md`, and are submitted on paper on October 1, 2026.
- Two AI models each produce an independent document set, isolated on the `claude` and `agy` git branches; `main` is the shared base.
- The product name is not yet chosen, and the second of the two required products is not yet selected. Both must be deferrable without invalidating the documents written now.
- No Confluence, Jira, or other requirements tool is available to the team.

## Goals / Non-Goals

**Goals:**

- Make the authoring conventions for each document type machine-readable, so later edits by a teammate or an agent are checked rather than remembered.
- Keep the conventions durable and the content separate, so the rules survive the archival of this change.
- Use one mechanism for documentation now and code later, so Milestone 2 adds capabilities beside these rather than replacing them.
- Keep both model branches governed by identical rules, so differences in output are attributable to the models.

**Non-Goals:**

- Writing the document content. That is this change's implementation output, produced during apply.
- Specifying the finance tracker product itself. Its capabilities are separate changes at Milestone 2.
- Automated enforcement. These specs are read and applied by people and agents; no linter is built.

## Decisions

### Use the stock `spec-driven` schema rather than a custom one

The alternative was `openspec schema fork spec-driven product-docs` with artifacts named `vision`, `personas`, `one-pagers`, and `sizing`. This was investigated before being rejected:

- `openspec schema init --artifacts "vision,personas,..."` is refused outright: `{"error": "Unknown artifact 'vision'", "valid": ["proposal","specs","design","tasks"]}`.
- Forking and hand-editing `schema.yaml` with custom artifact IDs does validate and run end to end, but every schema command prints *"Schema commands are experimental and may change."*

Beyond the stability concern, the fork approach conflates two different things: it would make each document type an *artifact of a change*, when what is durable is the *rule* for writing that document type. The stock schema expresses this correctly — the rules are specs, the documents are the change's output.

### Specs govern documents; `docs/` holds document content

`openspec/changes/` is temporary and is archived once a change completes; `openspec/specs/` is permanent and is what every later change consults. Document content therefore cannot live in the change directory, or it disappears from the working set when this change is archived. The split is: `openspec/specs/documentation/**` holds how to write, read, and update each document type; `docs/**` holds the documents themselves.

A consequence worth stating: for this change, the documentation *is* the implementation. Apply produces Markdown under `docs/`, not code.

### Seven capabilities, namespaced under `documentation/`

The alternative was four capabilities, folding `user-stories` and `requirements-sizing` into `one-pagers` as sections of that template. Seven was chosen because the story format and the sizing protocol are reused outside 1-pagers — stories become backlog items and sizing drives sprint commitment at Milestone 2 — and a capability that other capabilities depend on should not be a subsection of one of them.

The `documentation/` path segment namespaces these away from the code capabilities that will be added later, so `openspec/specs/` does not become a flat mix of process rules and product behaviour.

### Narrative scenarios and spec scenarios are kept distinct

Two different things are called a "scenario" in this project, and conflating them would fail the rubric:

| | Sommerville scenario | OpenSpec `#### Scenario:` |
|---|---|---|
| Form | Narrative prose, 1–2 paragraphs | Structured **WHEN** / **THEN** |
| Lives in | A 1-pager's PROBLEM section | `specs/**/spec.md` |
| Purpose | Stimulate thinking, communicate to non-engineers | Testable behaviour contract |

The `one-pagers` capability therefore requires PROBLEM to be continuous prose and explicitly forbids WHEN/THEN there — even though the spec that states this rule is itself written in WHEN/THEN. Structured scenarios are known to read as intimidating to the non-engineer readers who check scenarios, which is precisely why the narrative form is mandated for the graded document.

### Markdown in git, not a requirements tool

Git supplies what the rubric needs and a wiki would not: the draft history of the vision is a graded artifact, and commits make each revision attributable and dated. Printing to PDF for the October 1 submission is a straightforward final step.

### Branch-based model isolation, no per-model directories

Given that each model's work is already isolated on its own branch, per-model subdirectories under `docs/` would duplicate that separation and invite cross-contamination. The layout is identical on every branch; the branch is the discriminator.

This makes one sequencing requirement load-bearing: the rules must be identical on both branches, or the two document sets are not comparable and the model critique is unsound.

## Risks / Trade-offs

- **The rules diverge between branches** → This change must land on `main` and be merged into both `claude` and `agy` before document authoring begins on either. If the specs are edited on one branch only, the comparison measures differing instructions rather than differing models.

- **Process rules become bureaucratic and slow the work** → Every requirement here traces to either a rubric item in `project1.md` or a named constraint from Sommerville Ch3. A rule that traces to neither should be removed rather than followed.

- **Seven documentation capabilities crowd out code capabilities at Milestone 2** → The `documentation/` namespace keeps them separable, and they are stable once written; they are read far more often than edited.

- **Eleven days remain before the October 1 submission** → The specs are deliberately short and checkable. The costly work is the document content, and the task breakdown sequences it so the graded artifacts for the first product are complete before the second product is started.

- **Specs are enforced by reading, not tooling** → `openspec validate` checks structure, not compliance of a document with its rule. Compliance is a review step, which the task breakdown makes explicit rather than implicit.

## Open Questions

These can be answered later without changing the specs, the approach, or the task breakdown:

- **The product name.** The `doc-structure` capability mandates the `{{PRODUCT_NAME}}` placeholder and a single substitution pass, so the name can be chosen at any point before submission.
- **The second product** from the four options in `project1.md`. The per-product directory layout is already defined, so adding it is a sibling directory rather than a restructuring.
