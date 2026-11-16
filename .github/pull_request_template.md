<!--
Rules: openspec/specs/process/branching-and-releases and openspec/specs/process/backlog-flow.
For a story (feature/ branch), fill in every section. For bug/, spec/, docs/, and chore/
branches, delete the sections that do not apply.
-->

## What this merges

- **Branch type:** feature / bug / spec / docs / chore
- **Story:** `<NN>-S<NN>` — <!-- the story's "I want to" clause; for a bug, the story whose behavior it fixes -->
- **OpenSpec change:** `openspec/changes/<change-name>/` <!-- archived path once archived; "none" for a bug that violates an existing scenario -->

## Slices

<!-- One line per slice, in order. Each slice is its own commit (scaffolding may be a separate commit within its slice). -->

1. Slice 1: <observable behavior> — <commit>
2. Slice 2: <observable behavior> — <commit>

## Demo steps

<!-- How a reviewer sees the whole story working, end to end. -->

1.

## Definition of Done

- [ ] Every task in the change is complete and every automated test passes
- [ ] `openspec validate <change-name> --strict` passes
- [ ] Every applicable non-functional requirement from the 1-pager is met, or deferred to a follow-up story recorded in the 1-pager and named in `design.md`
- [ ] `docs/architecture.md` is updated, or the change made no structural decision
- [ ] The change is archived on this branch
- [ ] The status table in `docs/README.md` is refreshed on this branch
- [ ] The story is removed from `docs/backlog.md` on this branch

## After merging

- [ ] Merged with a merge commit (not squash, not rebase)
- [ ] Merge commit tagged: `feature/` bumps MINOR, anything else bumps PATCH

```sh
git switch develop && git pull
git tag -a vX.Y.Z -m "vX.Y.Z — <NN>-S<NN> <title> | <branch name>"
git push origin vX.Y.Z
```
