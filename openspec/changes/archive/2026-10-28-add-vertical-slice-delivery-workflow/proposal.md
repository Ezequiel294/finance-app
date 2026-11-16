## Why

The requirements side of the product is defined: a vision, five personas, seven 1-pagers, fifty-two user stories with stable identifiers, and a sizing protocol. Nothing yet defines how a story becomes working software. Without that, the default is to build each layer in bulk — the whole database, then the whole backend, then the whole interface — and to discover only at the end whether the pieces fit, with a diff too large for anyone to review honestly. A review that cannot be done properly is approved anyway, which is the same as no review.

The alternative is to deliver each story as a sequence of thin vertical slices, each carrying the minimum of every layer needed for one observable behavior, each leaving the product working, and each reviewed on its own. That only holds if it is written down where every future change will see it: the proposal, spec, and task artifacts of every change are generated from this project's specs and configuration, so a rule that lives only in conversation will not shape them.

## What Changes

- Introduce a **process capability family** under `specs/process/` defining how stories are delivered, how work is ordered and limited, how branches and versions are managed, and how product capability specs are organized.
- Define that **one OpenSpec change realizes exactly one story**, and that its `tasks.md` is a sequence of **vertical slices** whose boundaries are chosen per story, each tested on its own and against the slices before it, and each reviewed before the next begins.
- Define a **continuous flow** in place of sprints: an ordered backlog that never records status, a limit of one active story per person, a Definition of Ready, a Definition of Done, and spikes for unverified assumptions.
- Define **branching, pull requests, and versioning**: `main` as production moved only by fast-forward to a version tag, `develop` as integration, prefixed work branches, merge-commit-only PRs, and a semver tag on every merge into `develop`.
- Define that **product capability specs are organized by epic and capability**, not by story, so the current behavior of an area of the product is read in one place.
- Narrow derived implementation status to **product capability specs**, so a process or documentation spec that mentions a story identifier cannot mark it implemented.
- Add `docs/backlog.md`, admit `docs/architecture.md` to the document layout, add per-artifact rules and operation guidance to `openspec/config.yaml`, and add a pull request template.
- **No application code is written by this change.**

## Capabilities

### New Capabilities

- `process/vertical-slices`: One change per story; story detail bullets become spec scenarios; tasks organized as ordered vertical slices, each test-first, each leaving the product working, each a separate commit and review checkpoint; tests that cover how later slices interact with earlier ones; foundations built only when a slice needs them.
- `process/backlog-flow`: The ordered backlog, the per-person limit on active stories, the Definition of Ready, the Definition of Done, and spikes as the way unverified assumptions are settled.
- `process/branching-and-releases`: The role of `main` and `develop`, work branch prefixes and naming, how bug fixes are named and when they need a change, pull request requirements by team size, merge-commit-only integration, semver tagging rules, and releasing by fast-forward.
- `process/capability-layout`: Where product capability specs live, what a capability is as opposed to a story, and how later epics modify a capability in place rather than duplicating it.

### Modified Capabilities

- `documentation/doc-structure`: **Document Set Layout** admits `backlog.md` and `architecture.md`.
- `documentation/user-stories`: **Implementation Status Is Derived From Specs** and **Specs Cite The Stories They Realize** apply to product capability specs only, excluding `documentation/` and `process/`. **Epics Are Recognised And Split Before Implementation** measures an epic against a single change rather than a sprint, since sprints are not used.

## Impact

- **New specs** under `openspec/specs/process/` once this change is archived.
- **`openspec/config.yaml`** gains `rules` for every artifact and `operations` guidance for apply and archive, so every later change is generated against this workflow.
- **New document** `docs/backlog.md`; `docs/README.md` index and a pointer to the process specs.
- **New file** `.github/pull_request_template.md`; `.gitignore` admits `.github/`.
- **Repository settings outside this change**: merge method and branch protection are configured on GitHub by hand; the specs state what they must be.
- **No runtime code, dependencies, or APIs are affected.** The first product change, for the first story in the backlog, establishes the stack.
