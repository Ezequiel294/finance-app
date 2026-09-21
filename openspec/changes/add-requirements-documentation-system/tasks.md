## 1. Establish The Rules On A Shared Base

- [ ] 1.1 Land this change (specs, proposal, design) on `main` and verify `git log main --oneline` shows the commit and `openspec validate add-requirements-documentation-system` passes from a `main` checkout
- [ ] 1.2 Merge `main` into `claude` and into `agy`, and verify `git diff main claude -- openspec/specs/documentation/` and `git diff main agy -- openspec/specs/documentation/` both report no output, so each model authors under identical rules
- [ ] 1.3 Add a `context` block to `openspec/config.yaml` naming the course, the rubric source `project1.md`, and `openspec/specs/documentation/` as the authoring rules, and verify `openspec instructions proposal --change add-requirements-documentation-system --json` now returns a populated `context` field

## 2. Scaffold The Documentation Tree

- [ ] 2.1 Create `docs/finance-tracker/` containing `drafts/` and `one-pagers/`, and `docs/evaluation/`, and verify the tree matches the layout required by `documentation/doc-structure`
- [ ] 2.2 Create `docs/README.md` with the document index and a table mapping every rubric item in `project1.md` to the file satisfying it, marking unsatisfied items as open, and verify every listed path exists
- [ ] 2.3 Move `llm-prompts.md` to `docs/evaluation/prompt-log.md`, reformatting existing entries to carry verbatim prompt, model, date, and documents affected, and verify no prompt log remains at the repository root
- [ ] 2.4 Record the undecided second product as an open item in `docs/README.md` and verify it appears in the rubric mapping table as unsatisfied

## 3. Product Vision

- [ ] 3.1 Write `docs/finance-tracker/vision.md` using all six Moore clauses with `{{PRODUCT_NAME}}` in the THE clause, and verify each of the six clause keywords appears exactly once
- [ ] 3.2 Save the exploration-stage vision wording as `docs/finance-tracker/drafts/vision-v1.md` with a note on what changed between it and the current version, and verify the draft file is present and referenced from the index
- [ ] 3.3 Review the vision against `documentation/product-vision` and verify it names a real competitive alternative in UNLIKE, enumerates no features, and answers what, who, and why on its own

## 4. Personas

- [ ] 4.1 Write `docs/finance-tracker/personas.md` with four personas — the multi-account multi-currency primary user, the single-bank simplicity anchor, the credential-averse household budgeter, and the irregular-income earner — and verify each is two to three paragraphs
- [ ] 4.2 Verify every persona covers personalization, job, education, and relevance, and that no persona states goals, per `documentation/personas`
- [ ] 4.3 Label each persona with its grounding — real user data or proto-persona — and verify the primary persona cites the behaviour documented in `Inversiones.xlsx` and the stated account topology
- [ ] 4.4 Add the documented-omissions section naming the excluded user types and the reason for each, and verify at least the financial advisor and bank operations exclusions are covered
- [ ] 4.5 Verify each persona pulls at least one requirement no other persona pulls, and record that distinguishing requirement alongside each persona

## 5. One-Pagers

- [ ] 5.1 Write `one-pagers/01-accounts-and-transaction-ingestion.md` covering connection, import, manual entry, and duplicate handling, and verify the BAC developer-portal finding and the aggregator coverage gap appear in ASSUMPTIONS with sources and dates
- [ ] 5.2 Write `one-pagers/02-categorization-and-rules.md` covering automatic categorization and the independent category and spending-group dimensions, and verify at least one story covers tagging a charge at the time it occurs
- [ ] 5.3 Write `one-pagers/03-budgets-and-limits.md` covering per-group limits, alerts, and safe-to-spend for the month, and verify both the steady-income and irregular-income personas appear as story subjects
- [ ] 5.4 Write `one-pagers/04-dashboard-and-insights.md` covering the spending charts and transaction views from the baseline product idea, and verify every chart story states what question the chart answers
- [ ] 5.5 Write `one-pagers/05-multi-currency-and-fx.md` covering colones and dollars, rate sourcing, account roles, and exclusion of transfers between the user's own accounts, and verify the BCCR and Hacienda rate APIs are recorded in ASSUMPTIONS with sources
- [ ] 5.6 Write `one-pagers/06-security-and-data-control.md` covering authentication, encryption, consent, and revocation, and verify the credential-averse persona's constraint is stated as a positive story about control rather than a negative story
- [ ] 5.7 Write `one-pagers/07-investments-and-net-worth.md` covering manual holdings, live price lookup, the configurable fee profile, and net liquidation value, and verify the deposit, per-trade, and withdrawal fee types from `Inversiones.xlsx` are all represented and that no multi-participant pooling appears
- [ ] 5.8 Verify every 1-pager carries all five required sections with the exact template headings in order, and that every PROBLEM section is one to two paragraphs of continuous prose containing no bullets or WHEN/THEN clauses
- [ ] 5.9 Verify every functional requirement uses the full story format with a persona defined in `personas.md`, and that every persona is the subject of at least one story somewhere

## 6. Sizing

- [ ] 6.1 Choose and publish the baseline anchor story with its point value in `docs/finance-tracker/sizing.md`, and verify the anchor is one of the stories written in section 5
- [ ] 6.2 Size every functional requirement in every 1-pager on the 1/2/3/5/8/13 scale with a written rationale naming the driving dimensions and the comparison made, and verify no story lacks a rationale
- [ ] 6.3 Split any story sized at 13 into smaller stories, size each independently, and verify no 13 remains in any 1-pager
- [ ] 6.4 Add the estimate-uncertainty statement to `sizing.md` and verify it states these are first-pass relative estimates from a team with no velocity history
- [ ] 6.5 Build the roll-up table in `sizing.md` listing every story with its size and 1-pager, and verify equally sized stories across different 1-pagers represent comparable effort

## 7. Compliance Review And Handoff

- [ ] 7.1 Review the complete document set against each of the seven `documentation/` specs in turn and verify every requirement's scenarios are satisfied, recording any deviation found and corrected
- [ ] 7.2 Verify `docs/README.md` lists every file present under `docs/` and that its rubric mapping leaves no `project1.md` rubric item unaccounted for
- [ ] 7.3 Update `docs/evaluation/prompt-log.md` with the prompts used to produce this document set, each with its effectiveness note, and verify no document in the set was produced by an unlogged prompt
- [ ] 7.4 Confirm the document set is sufficient for Milestone 2 handoff by verifying every 1-pager's functional requirements could be promoted to code capability specs without further elicitation
