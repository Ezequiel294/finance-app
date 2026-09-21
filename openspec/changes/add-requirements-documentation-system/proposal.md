## Why

This product is defined by a set of documents before it is defined by any code: a product vision, personas, 1-pagers describing each initiative, the user stories that make up their functional requirements, and the effort sizing attached to those stories. These documents are not a one-time deliverable. They are the standing description of what the product is for and who it serves, and they will be read, revised, and argued with for as long as the product is developed.

Documents like these drift when the conventions behind them live only in people's heads. Personas accumulate until they overlap and stop being useful. A problem statement quietly turns into a specification. Sizes get assigned with no reasoning anyone can reconstruct later. A story gets built and nobody can tell afterwards which ones are done. Writing the conventions down as specifications makes them checkable: any contributor, and any tool, can verify a document against the rule it is supposed to follow instead of guessing at house style.

## What Changes

- Introduce a **documentation capability family** under `specs/documentation/` defining how each document type is written, read, and updated.
- Establish `docs/` as the home for document content, with a defined layout, naming convention, and index.
- Define what makes a persona useful and bounded: how many there may be, what each must contain, what must never appear in one, and which user types were deliberately excluded.
- Define the 1-pager structure, and require its problem statement to be a narrative account of a person trying to do something rather than a specification of system behavior.
- Define the user story format, and define how a story's implementation status is derived from the specs rather than tracked separately, so the project needs no external board to answer what is built and what is not.
- Define the sizing protocol: the metric, its scale, the baseline every estimate is compared against, and the reasoning each estimate must carry.
- **No application code is written by this change.** Its output is Markdown under `docs/`.

## Capabilities

### New Capabilities

- `documentation/doc-structure`: Where documentation lives, how files are named, how the index is maintained, and how a reader determines which documented requirements are already built.
- `documentation/product-vision`: How the product vision is written, how superseded versions are retained with the reasoning behind each change, and how the vision governs whether a proposed feature belongs in the product.
- `documentation/personas`: How personas are authored — count ceiling, required aspects, prohibited content, grounding, and documented omissions — and how the set is revised when a new persona is proposed.
- `documentation/one-pagers`: The required structure of a 1-pager, what belongs in each section, and what makes a problem statement a narrative scenario rather than a specification.
- `documentation/user-stories`: The story format, stable story identifiers, the lifecycle of a story from written to built or withdrawn, and how implementation status is derived from the specs.
- `documentation/requirements-sizing`: The effort metric, its scale, the published baseline anchor, the dimensions each estimate is scored on, and the rationale every size must carry.

### Modified Capabilities

None. This is the first capability set in the project; `openspec/specs/` is currently empty.

## Impact

- **New directory** `docs/` holding all product document content.
- **New specs** under `openspec/specs/documentation/` once this change is synced.
- **A convention that outlives this change**: capability specs written during development cite the story identifiers they realize, which is what makes implementation status derivable rather than separately tracked.
- **No runtime code, dependencies, or APIs are affected.** Product capabilities will be added as separate changes when development begins.
