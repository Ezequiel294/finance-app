## Context

See `proposal.md` — Why. The constraints that shape this design:

- The product is built by one or two people, each working with an AI assistant that writes most of the code. The binding constraint is not typing speed but how much a person can review properly.
- There is no business pressure on delivery dates and no external stakeholder expecting sprint ceremonies.
- Story status is already derived from the specs (`documentation/user-stories`). Anything added here has to keep that mechanism truthful rather than introduce a second tracker.
- Every change's artifacts are generated from the project's specs and from `openspec/config.yaml`. A rule that lives in neither will not shape them.
- The repository is on GitHub with `main`, `develop`, and an annotated tag `v0.0.1` on the first merge into `develop`. The GitHub CLI is not installed, so repository settings are configured by hand.
- No application code exists yet, and no stack has been chosen.

## Goals / Non-Goals

**Goals:**

- Make every review small enough to be done properly, by construction rather than by discipline.
- Keep the product working after every slice, so integration problems surface in the slice that causes them.
- Keep derived status exact: a story reads as implemented only when all of it is.
- Make the product specs readable by someone joining later, one area of behavior at a time.
- Make every integrated change traceable to a version, and production to exactly one version.

**Non-Goals:**

- Choosing the stack. The first product change does that in its own design.
- Automated enforcement. No CI checks, hooks, or linters are built here; the rules are applied through artifact generation and review.
- Configuring GitHub. The specs state what the settings must be; applying them is a manual step outside the change.
- Velocity, burndown, or any schedule derived from story points.

## Decisions

### One change per story, not per epic

The alternative was one change per epic, with tasks divided first by story and then by slice. It was rejected for four reasons.

- **Upfront scope.** The largest epic holds twelve stories and fifty-two points. Writing all of its specs, design, and tasks in one proposal is big design up front, and the specs for the tenth story would be stale before work reached it.
- **Status.** A change cites every story it covers. Under per-epic changes, every story in the epic reads as in progress from the first day, and nothing reaches `openspec/specs/` until the last story is finished.
- **Blocking.** Some stories rest on unverified assumptions and may prove unbuildable. In a per-epic change, one of those would hold the whole epic's archive hostage.
- **Ordering.** The most useful first path through the product crosses epics: capture, then organize, then review. Per-epic changes would leave several half-finished epics open at once, which is horizontal slicing one level up.

The epic's motivation already exists as its 1-pager, so a per-epic proposal would mostly repeat it.

### Slices live inside a story's tasks, with no size threshold

A size cap — for example, splitting every story above five points — was considered and rejected. The right cut depends on the story: a two-point story may still need two slices to stay reviewable, and an eight-point story may slice cleanly into four. Slice boundaries are therefore chosen when the story's tasks are written, and corrected during review if a slice turns out too large.

Because slices are task groups within one change rather than separate changes, derived status stays exact. A story whose first two slices are built is still in progress, which is true. Had slices been separate changes, the first slice's archive would have marked the whole story implemented.

### Two review points per story

The first review is of the planning artifacts, before any code exists. It is short — a delta spec and a slice plan — and it is the cheapest place to change what gets built or where the slices fall. The second is per slice: one commit, one small diff, one set of demo steps. The assistant stops after each slice, which is set in `operations.apply.guidance` so it applies to every change without being restated.

### Specs organized by epic and capability, not by story

Three layouts were considered: one spec per story; one folder per epic with a folder per story inside it; and one folder per epic with a spec per capability inside it.

A story is a request to change behavior, not a part of the system, and later stories change what earlier ones built. Under either story-based layout, the current behavior of something like manual entry would be scattered across every story that has touched it. A capability spec keeps that behavior in one file, with each requirement citing every story that shaped it. That citation is also what keeps derived status working.

The epic folder uses the 1-pager's slug without its ordinal, because the documentation rules allow ordinals to be renumbered and spec paths should not move when they are.

### A living architecture document alongside the specs

OpenSpec specs are behavior contracts and exclude frameworks and module names by design. The structural knowledge a new developer needs — the stack, the layers, the module map, and why — would otherwise exist only in the `design.md` of whichever archived change made each decision. `docs/architecture.md` collects it in one place, updated in the same change as the decision, linking back to that change.

### Continuous flow instead of sprints

Sprints exist to create a cadence for planning and commitment under delivery pressure. With one or two people and no external deadlines, they add ceremony without adding information. A continuous flow keeps the parts that matter: an order, a work-in-progress limit, entry and exit criteria, and spikes for uncertainty. The dated archive folders already give a delivery history that can be grouped by any period after the fact.

The documentation rules defined an epic as a story too large for a single sprint. With no sprints, that definition would point at nothing, so it is restated against the unit that does exist: a story too large to be delivered by a single change is an epic and is split before it is ordered or proposed.

The backlog lists only stories not yet implemented, and an archive removes its story from the backlog in the same commit. That removal is part of the same atomic step that makes the story implemented, so the two records cannot disagree for longer than an unmerged branch.

### Narrowing derived status to product specs

The status rule, as written, counted a story identifier cited by any requirement in `openspec/specs/`. Once process specs exist, an illustrative mention of an identifier there would mark a story implemented. The rule now counts product capability specs only, defined as everything outside `documentation/` and `process/`. The process specs written here use the placeholder `<NN>-S<NN>` throughout regardless.

### Branching: `main` moves only by fast-forward to a tag

Merging `develop` into `main` through a pull request creates a new merge commit on `main` that carries no tag, so production would never be exactly a tagged version. Fast-forwarding `main` to a tag avoids that: production is always precisely one version, and the tag is its identity.

No hotfix branches are defined. A fix goes through `develop` like everything else, and the cost — any other unreleased work on `develop` ships with it — is acceptable without delivery pressure. If that changes, a hotfix flow is a change to `process/branching-and-releases`.

### Merge commits only, and the merge commit is what gets tagged

Squash merging was rejected because it collapses a story's per-slice commits into one, destroying the history a reviewer reads slice by slice and a later reader uses to see how a behavior was built up. Rebase merging was rejected because it leaves no single commit representing the merge to tag.

### Semver bump rules keyed to the branch prefix

Bumps are decided mechanically by the branch prefix: a story merge increments MINOR; anything else increments PATCH. MAJOR stays at 0 until a deliberate decision to call a merge the first production release, which matches semver's meaning of 0.y.z as initial development. The existing `v0.0.1` — a documentation merge — already conforms, so this change will be `v0.0.2`.

### Rules in `config.yaml`, not a forked schema

Forking the `spec-driven` schema to change the tasks template was rejected for the same reason it was rejected for the documentation system: schema commands are experimental, and the stock schema already separates durable rules (specs) from per-change artifacts. `rules` and `operations` in `openspec/config.yaml` are injected into every artifact's instructions and into apply and archive, which is all this workflow needs.

### Approval rules that GitHub can actually enforce

GitHub does not allow the author of a pull request to approve it. "Self-approval" for a solo contributor is therefore expressed as zero required approvals in branch protection, with the per-slice reviews serving as the review. The requirement to raise approvals to one when a second contributor joins is stated as a scenario so it is not forgotten.

## Risks / Trade-offs

- **The assistant does not stop after a slice** → `operations.apply.guidance` is advisory to the apply workflow, not enforced. The first product change's apply is the test of it; if it does not hold, the guidance is strengthened or moved into a project instruction file.
- **Slices become ceremony for trivial stories** → No minimum slice count is set. A story small enough to be one observable behavior is one slice.
- **The backlog drifts from the specs** → Removal happens in the archive commit, and the specs are defined as authoritative when the two disagree.
- **Every merge is tagged by hand** → Tagging is a manual step after each merge and can be forgotten. A missed tag is visible in `git log --first-parent develop` and can be added afterwards without moving any existing tag. Automating it is a later `chore/` change.
- **No hotfix path** → Unreleased work on `develop` ships with any fix. Accepted while there is no delivery pressure.
- **Process rules outgrow the product** → Every rule here traces to a failure mode named in this design. A rule that stops earning its place is removed through a `spec/` change rather than ignored.

## Migration Plan

- This change ships on `spec/process` and is merged into `develop` as `v0.0.2` under its own rules.
- GitHub settings are applied by hand after merging: merge commits only; a pull request required on `develop` with zero approvals while there is one contributor; direct pushes to `main` restricted to the repository owner.
- No existing document or spec content is invalidated. The status table still reports all fifty stories not started.

## Open Questions

Deferrable without changing the specs, the approach, or the task breakdown:

- **Automating the version tag.** A GitHub Action could tag each merge into `develop` from its branch prefix. Worth doing once merges are frequent enough for a missed tag to matter.
- **Where the app displays its version.** Decided by the first product change along with the stack.
