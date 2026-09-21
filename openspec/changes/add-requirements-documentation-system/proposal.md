## Why

CS 3365 Project 1 is graded on requirements documentation — product visions, personas, 1-pagers, functional requirements, and sizing — turned in on October 1, 2026. Those documents must follow specific, checkable conventions (Sommerville *Engineering Software Products* Ch3 for personas and scenarios; the 1-pager template at the end of `project1.md`), and they will be revised repeatedly across two products and two AI models before submission.

Without a written contract for how each document type is structured, drift is inevitable: personas grow past five, a PROBLEM section turns into a bullet list, sizing gets assigned with no stated rationale. This change makes those conventions machine-readable specs so every later edit — by a teammate or an AI agent — is checked against the same rules, and so the same mechanism extends to code specs when development starts at Milestone 2.

## What Changes

- Introduce a **documentation capability family** under `specs/documentation/` that defines how each Project 1 artifact type is written, read, and updated.
- Establish `docs/` as the home for actual document content, with a defined layout, naming convention, and index.
- Encode the Sommerville Ch3 constraints as testable requirements: persona ceiling and required aspects, narrative (not structured) scenarios, the user-story format, the ban on negative stories in a backlog.
- Encode the `project1.md` 1-pager template as a structural requirement so section headings and ordering cannot drift.
- Define the sizing protocol — metric, scale, baseline anchor, and the rationale each estimate must carry.
- Define how AI interactions are logged and how the cross-model critique is produced, given that each model's work lives on its own git branch.
- **No application code is written by this change.** Its implementation output is Markdown under `docs/`.

## Capabilities

### New Capabilities

- `documentation/doc-structure`: Where documentation lives, how files and directories are named, how the index and traceability map are maintained, and how per-product and per-model isolation works across git branches.
- `documentation/product-vision`: How a product vision is written (Moore template), how drafts are retained as graded evidence, and how the vision is revised without losing its history.
- `documentation/personas`: How personas are authored — count ceiling, required aspects, prohibited content, documented omissions — and how the set is revised when a new persona is proposed.
- `documentation/one-pagers`: The required structure of a 1-pager, what belongs in each section, and what makes a PROBLEM section a properly written Sommerville scenario rather than a specification.
- `documentation/user-stories`: The story format used inside 1-pagers and reused later as backlog items, including supporting detail bullets and the handling of negative stories.
- `documentation/requirements-sizing`: The effort metric, its scale, the published baseline anchor, the dimensions each estimate is scored on, and the rationale that must accompany every size.
- `documentation/ai-interaction-log`: How prompts and model outputs are recorded, and how the comparative model critique is assembled from work that lives on separate branches.

### Modified Capabilities

None. This is the first capability set in the project; `openspec/specs/` is currently empty.

## Impact

- **New directory** `docs/` holding all Project 1 document content.
- **New specs** under `openspec/specs/documentation/` after this change is synced.
- **Existing file** `llm-prompts.md` at the repository root is superseded by the logging convention defined here and will be relocated under `docs/`.
- **Git branches**: `claude` and `agy` each carry one model's document set; `main` is where the cross-model critique is assembled. The `doc-structure` capability records this so the layout is not re-derived per branch.
- **No runtime code, dependencies, or APIs are affected.** Code capabilities will be added as separate changes at Milestone 2.
