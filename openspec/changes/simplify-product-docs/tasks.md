## 1. Move what personas enforced into the vision

- [x] 1.1 Add a **Principles** section to `docs/vision.md` with two principles that can be checked:
  - the product is fully usable without linking any account;
  - the product is useful with one account, one currency, and no setup.

  Verify that neither principle names a feature or a screen.
- [x] 1.2 Add a **Non-goals** section to `docs/vision.md`. Take the four items, and the reason for each, from the "Deliberately Not Personas" section of `docs/personas.md`:
  - financial advice or recommendations;
  - tax and accounting;
  - businesses and organisations;
  - running anything on a bank's or institution's side.

  Verify that all four appear, each with its reason.
- [x] 1.3 Rewrite the "Using This Vision" section:
  - a vision change is explained in its commit message, not saved in `drafts/`;
  - the check against the vision includes the principles and non-goals.

  Verify that `grep -n drafts docs/vision.md` finds nothing.
- [x] 1.4 Delete `docs/personas.md` and the `docs/drafts/` folder. Verify that `ls docs` shows neither.
- [ ] 1.5 Stop for review. After it is accepted, commit this group on its own.

## 2. Rename 1-pagers to epics (file moves and headings only, no rewording)

- [x] 2.1 Run `git mv docs/one-pagers docs/epics`. Verify that all seven files keep their numbers and names.
- [x] 2.2 In each epic:
  - change the title to just the initiative name, removing "— 1-Pager";
  - rename `### FUNCTIONAL REQUIREMENTS` to `### STORIES`;
  - delete the `### REQUIREMENTS SIZING` section.

  Verify that each file's `###` headings are exactly PROBLEM, ASSUMPTIONS, STORIES, NON-FUNCTIONAL REQUIREMENTS, in that order.
- [x] 2.3 Before rewording anything, save the list of story IDs in each epic to the scratchpad. Task 3.8 compares against this list. Verify that it holds 52 IDs.
- [ ] 2.4 Stop for review. After it is accepted, commit this group on its own.

## 3. Rewrite each epic as situations and job stories

Do the same steps in each epic:
- Rewrite PROBLEM as one or two paragraphs that describe situations. Name no people.
- Rewrite every story as **When** `<situation>`, **I want to** `<task>`, **so that** `<outcome>`. The situation describes the person's circumstances, not who they are.
- Keep each detail bullet's wording. Only remove persona names from it.
- Rewrite each split note as "Replaced by …", with no mention of size.
- Check the epic with `grep -nE 'Ezequiel|Daniela|Patricia|Andrés|Keisy|[Pp]ersonas?([^a-z]|$)|story points?|[0-9]+ points?|Sized at|baseline anchor' <file>`. It must find nothing. The pattern skips everyday words such as "personal" and "floating point".
- Stop for review after each epic. Commit each epic on its own.

- [x] 3.1 `01-accounts-and-transaction-ingestion.md`, including the split note on `01-S01`
- [x] 3.2 `02-categorization-and-rules.md`
- [x] 3.3 `03-budgets-and-limits.md`, including:
  - the split note on `03-S05`;
  - the nested-budgets assumption, which is now settled by asking people who budget over several periods at once.
- [x] 3.4 `04-dashboard-and-insights.md`, including the single-summary-view assumption, which now compares someone who wants one fact with someone who wants to compare and drill in
- [x] 3.5 `05-multi-currency-and-fx.md`
- [x] 3.6 `06-security-and-data-control.md`
- [ ] 3.7 `07-investments-and-net-worth.md`
- [ ] 3.8 Compare the story IDs in `docs/epics/` with the list saved in 2.3. Verify that all 52 are still there, none is renumbered, and both split stories still say "Replaced by".

## 4. Backlog, sizing, and index

- [ ] 4.1 Delete `docs/sizing.md`. Verify that it is gone.
- [ ] 4.2 Rewrite `docs/backlog.md`.
  - The intro says three things: the backlog holds only what comes next; a story's detail bullets are written when it is added; and a story leaves when its change is archived.
  - The table keeps the same six stories in the same order, with the columns `#`, `Story`, `I want to`, and `Why here`.
  - Remove the persona column, the "baseline anchor" wording for `01-S03`, and the whole "Not Yet Ordered" section.

  Verify that every ID listed exists in an epic.
- [ ] 4.3 Rewrite `docs/README.md`.
  - The index lists `vision.md`, `backlog.md`, and `epics/`, with a table of the seven epics.
  - Remove the entries for personas, sizing, and drafts.
  - Replace the status table with an "Implementation Status" section. It shows the two `grep` queries from `design.md` and points to `openspec list` for active work.
  - Add one line to "How Work Flows" saying that `documentation/epics` decides where new work goes.

  Verify that every file under `docs/` is in the index and that every link works.
- [ ] 4.4 Stop for review. After it is accepted, commit this group on its own.

## 5. Configuration, writing rules, and pull request template

- [ ] 5.1 Rewrite the documentation paragraph in the `context` of `openspec/config.yaml`. It describes the vision with its principles and non-goals, the epics in `docs/epics/`, and the backlog as the list of what comes next.

  Add a routing paragraph for explore to follow:
  - first check the vision;
  - if the idea is part of a story not yet built, add it to that story;
  - if an existing epic's PROBLEM covers it, add stories to that epic;
  - otherwise create a new epic;
  - decide by fit, not by size;
  - a story about to be built may be written into its epic as the first step of its change.

  Verify that `openspec instructions proposal --change simplify-product-docs --json` shows the new context.
- [ ] 5.2 Update the rules in `openspec/config.yaml`:
  - Proposal: `<epic-slug>` comes from the epic file in `docs/epics/`.
  - Proposal, new rule: if the story doesn't exist yet or has no detail bullets, write it into its epic first and commit it with the planning files.
  - Design: read the non-functional requirements from the story's epic.
  - Tasks, Done group: drop the status-table refresh, and remove the story from the backlog only if it is listed there.
  - Archive guidance: delete the status-table line, and remove the story from the backlog only if it is listed there.

  Verify that `grep -nE '1-pager|status table' openspec/config.yaml` finds nothing.
- [ ] 5.3 Add the writing rules to `openspec/config.yaml`, using this exact text.
  - In `context`: "Writing style for every change artifact: short sentences, one idea each. Everyday words; explain any term you must use. Active voice: say who does what."
  - Under `rules.proposal`:
    - "At most 250 words."
    - "Why: at most 3 sentences. What Changes: one line per change."
    - "Use bullets and tables, not paragraphs. Don't restate the story, the epic, or the specs; link to them."
  - Under `rules.design`:
    - "At most 500 words, not counting diagrams and tables."
    - "Decisions go in a table: Decision | Why | Rejected option. One short line per cell."
    - "Leave out any template section with nothing to say."
    - "Use bullets and tables, not paragraphs. Don't restate the story, the epic, or the specs; link to them."
    - "For a story change, include at least one Mermaid sequence diagram of the story's main flow, from the person through each layer and back."
  - Under `rules.specs`: "Use plain wording, but never drop a requirement, scenario, or detail to make a spec shorter. Covering everything matters more than length."
  - Under `rules.tasks`: "Use plain wording, but keep every step and its verification. Covering everything matters more than length."

  Verify that `openspec instructions design --change simplify-product-docs --json` lists the new design rules, and that the same command for `proposal`, `specs`, and `tasks` lists theirs.
- [ ] 5.4 Update `.github/pull_request_template.md`:
  - delete the status-table checkbox;
  - change "1-pager" to "epic";
  - change backlog removal to "if listed".

  Verify that `grep -nE '1-pager|status table' .github/pull_request_template.md` finds nothing.
- [ ] 5.5 Stop for review. After it is accepted, commit this group on its own.

## 6. Done

- [ ] 6.1 Search every tracked file outside `openspec/` with `git grep -nE 'Ezequiel|Daniela|Patricia|Andrés|Keisy|[Pp]ersonas?([^a-z]|$)|1-pager|one-pagers/|sizing\.md|drafts/|story points?|status table' -- ':!openspec'`. Verify that it finds nothing.
- [ ] 6.2 Run `openspec validate simplify-product-docs --strict`. Verify that it passes.
- [ ] 6.3 Run `openspec archive simplify-product-docs --yes`. Verify two things: `openspec/specs/documentation/` holds only `doc-structure`, `product-vision`, and `epics`; and `openspec validate --all --strict` passes.
- [ ] 6.4 Update the Purpose section of two specs by hand, because a delta can't change it:
  - `openspec/specs/documentation/doc-structure/spec.md`: where the documentation lives, how it is named and indexed, and how references stay valid;
  - `openspec/specs/documentation/product-vision/spec.md`: how the vision, its principles, and its non-goals are written, and how every epic and story is checked against them.

  Verify that `openspec validate --all --strict` still passes.
- [ ] 6.5 Search the specs with `grep -rnE 'Ezequiel|Daniela|Patricia|Andrés|Keisy|[Pp]ersonas?([^a-z]|$)|1-pager|one-pagers/|sizing\.md|drafts/|story points?' openspec/specs`, and run the two status queries from `design.md`. Verify that the search finds nothing and that both queries return nothing, since no story is built yet.
- [ ] 6.6 Stop for review. After it is accepted, commit the archive on its own.
