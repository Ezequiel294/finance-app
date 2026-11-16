## 1. OpenSpec Configuration

- [x] 1.1 Add a paragraph to the `context` block of `openspec/config.yaml` naming the delivery workflow and pointing at `openspec/specs/process/`, and verify `openspec instructions proposal --change add-vertical-slice-delivery-workflow --json` returns it in `context`
- [x] 1.2 Add `rules` for `proposal`, `specs`, `design`, and `tasks` that carry the one-story-per-change, scenario-per-bullet, slice-structure, and capability-layout requirements, and verify `openspec instructions tasks --change add-vertical-slice-delivery-workflow --json` returns the tasks rules in `rules`
- [x] 1.3 Add `operations.apply.guidance` (one slice at a time, commit per slice, stop for review with a per-layer summary) and `operations.archive.guidance` (status table, backlog removal), and verify `openspec instructions apply --change add-vertical-slice-delivery-workflow --json` returns them in `operationGuidance`

## 2. Documents

- [x] 2.1 Write `docs/backlog.md` with the suggested first path through capture, organize, and review at the top and every remaining story under an unordered heading in 1-pager order, and verify every story that carries an estimate appears exactly once and neither split parent appears
- [x] 2.2 Add `backlog.md` to the index in `docs/README.md` and a short section pointing to `openspec/specs/process/` for how work flows, and verify every file under `docs/` is listed in the index and no listed file is missing

## 3. Repository Plumbing

- [x] 3.1 Add `!.github/` to the `.gitignore` allowlist, and verify `git check-ignore .github/pull_request_template.md` reports nothing
- [x] 3.2 Write `.github/pull_request_template.md` with story and change, slices with one commit each, demo steps, and a Definition of Done checklist, and verify every Definition of Done condition in `process/backlog-flow` appears as a checklist item

## 4. Review And Archive

- [x] 4.1 Run `openspec validate add-vertical-slice-delivery-workflow --strict` and verify it reports the change valid
- [x] 4.2 Read the four `process/` delta specs against each other and against the `documentation/` specs, and verify no requirement contradicts another, recording and correcting any that does
- [x] 4.3 Archive the change, and verify `openspec list --specs` shows `process/vertical-slices`, `process/backlog-flow`, `process/branching-and-releases`, and `process/capability-layout`, and that the modified `documentation/` requirements carry the new text
- [x] 4.4 Verify `grep -rE '[0-9]{2}-S[0-9]{2}' openspec/specs` returns nothing, so the status table in `docs/README.md` correctly still reports all fifty stories not started
