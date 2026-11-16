# process/branching-and-releases Specification

## Purpose
Defines how code moves through the repository: the roles of `main` and `develop`, how work branches are named, what a pull request requires, how merges are made, how every integrated change is versioned, and how a version is released to production.

## Requirements

### Requirement: Main Is Production And Moves Only By Fast-Forward

`main` SHALL represent production and SHALL only ever point at a commit carrying a version tag. It SHALL move only by fast-forward to a version tag on `develop`. Commits and merges MUST NOT be made on `main` directly, and there SHALL be no release or hotfix branches.

#### Scenario: A version is released

- **WHEN** a tagged version on `develop` is chosen for production
- **THEN** `main` MUST be fast-forwarded to that tag and pushed, so production is always exactly one tagged version

#### Scenario: A fix is needed in production

- **WHEN** production needs a fix
- **THEN** the fix MUST go through a `bug/` branch from `develop`, be merged and tagged there, and reach production by fast-forwarding `main` to the new tag, accepting that any other work already on `develop` is released with it

### Requirement: Develop Is Integration

Every work branch SHALL start from `develop` and SHALL return to it only through a pull request.

#### Scenario: A branch is started from another work branch or from main

- **WHEN** a work branch is created from anything other than `develop`
- **THEN** it MUST be rebased onto `develop` before its pull request is opened

### Requirement: Work Branch Naming

Every work branch SHALL be named with one of these prefixes:
- `feature/<change-name>` for a story, where `<change-name>` is that story's change name;
- `bug/<story-id>-<slug>` for a fix to a story's behavior, or `bug/<slug>` when no story applies;
- `spec/<slug>` for changes to `process/` or `documentation/` specs;
- `docs/<slug>` for edits to documents only;
- `chore/<slug>` for tooling, dependencies, or configuration with no change in behavior.

Story identifiers in branch names SHALL be lowercase.

#### Scenario: A branch has no recognized prefix

- **WHEN** a work branch is named without one of the defined prefixes
- **THEN** it MUST be renamed before its pull request is opened, because the prefix decides how the merge is versioned

#### Scenario: A story's branch and change names differ

- **WHEN** a `feature/` branch name differs from the change it carries
- **THEN** the branch MUST be renamed to match, so branch, change, and archive folder can each be found from the others

### Requirement: Bug Fixes Borrow The Story They Break

A bug fix SHALL be named after the story whose specified behavior it corrects. Whether it needs an OpenSpec change depends on whether the spec or the code was wrong.

#### Scenario: The code violates an existing scenario

- **WHEN** the product behaves contrary to a scenario already in `openspec/specs/`
- **THEN** the fix needs no OpenSpec change, and MUST include a regression test that reproduces the bug and is named after the violated scenario

#### Scenario: The spec itself was wrong or silent

- **WHEN** the product behaves as specified but the specified behavior is wrong, or the spec says nothing about the case
- **THEN** the fix MUST be an OpenSpec change whose delta modifies or adds a requirement citing the story

### Requirement: Pull Requests Into Develop

Every merge into `develop` SHALL go through a pull request whose description follows the repository's pull request template. A story's pull request SHALL be opened as a draft once its change's planning artifacts are committed. With two or more contributors, branch protection on `develop` SHALL require at least one approval from someone other than the author. With a single contributor, no approval SHALL be required and the author merges their own pull request.

#### Scenario: Only one person is working on the product

- **WHEN** a single contributor opens a pull request
- **THEN** it MUST still be opened and merged as a pull request, and the per-slice reviews required by `process/vertical-slices` serve as its review, since the hosting service does not let an author approve their own pull request

#### Scenario: A second contributor joins

- **WHEN** a second person starts contributing
- **THEN** branch protection on `develop` MUST be raised to require one approval before their next pull request is merged

### Requirement: Merge Commits Only

Pull requests SHALL be merged with a merge commit. Squash merging and rebase merging MUST be disabled in the repository settings.

#### Scenario: A pull request is squash-merged

- **WHEN** a pull request would be squash-merged
- **THEN** it MUST be merged with a merge commit instead, because squashing collapses the one-commit-per-slice history that reviewers and later readers rely on, and leaves no single merge commit to tag

### Requirement: Specs And Code Arrive Together

For a story change, archiving the change, refreshing the `docs/README.md` status table, and removing the story from the backlog SHALL be committed on the work branch before it is merged, so that `develop` receives the implementation and the updated specs in the same merge.

#### Scenario: A story is merged without its archive commit

- **WHEN** a story's work branch is merged while its change is still active
- **THEN** the story reads as in progress on `develop` despite being built, and the archive MUST follow in a further pull request

### Requirement: Every Merge Into Develop Is Tagged

Every merge commit on `develop` SHALL receive an annotated tag of the form `v<MAJOR>.<MINOR>.<PATCH>`, never moved or reused once pushed:
- a merge from a `feature/` branch increments MINOR and resets PATCH;
- a merge from any other branch increments PATCH;
- MAJOR is incremented only by deliberate decision. It stays at 0 during initial development, and `v1.0.0` is reserved for the merge intended as the first production release.

The tag message SHALL name what was merged: the story identifier and title for a story, or the branch name otherwise. The version the application reports SHALL be derived from the tag at build time, and MUST NOT be maintained by hand in the source.

#### Scenario: A story is merged

- **WHEN** a `feature/` branch is merged into `develop` at `v0.1.4`
- **THEN** its merge commit MUST be tagged `v0.2.0`

#### Scenario: A non-story branch is merged

- **WHEN** a `bug/`, `spec/`, `docs/`, or `chore/` branch is merged into `develop` at `v0.2.0`
- **THEN** its merge commit MUST be tagged `v0.2.1`

#### Scenario: A manifest requires a version field

- **WHEN** a build tool requires a version number in a source file
- **THEN** that field MUST hold a fixed placeholder and the reported version MUST come from the tag, so there is one record of the version rather than two that can disagree
