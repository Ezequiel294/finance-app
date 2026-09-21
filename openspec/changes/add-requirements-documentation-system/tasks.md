## 1. Scaffold The Documentation Tree

- [ ] 1.1 Add a `context` block to `openspec/config.yaml` naming the product domain and pointing at `openspec/specs/documentation/` as the authoring rules, and verify `openspec instructions proposal --change add-requirements-documentation-system --json` returns a populated `context` field
- [ ] 1.2 Create `docs/` containing `one-pagers/` and `drafts/`, and verify the tree matches the layout required by `documentation/doc-structure`
- [ ] 1.3 Create `docs/README.md` with the document index and an empty implementation status table, and verify every path it lists exists

## 2. Product Vision

- [ ] 2.1 Write `docs/vision.md` using all six clauses of the vision template with `{{PRODUCT_NAME}}` in the naming clause, and verify each of the six clause keywords appears exactly once
- [ ] 2.2 Save the earlier exploration-stage wording as `docs/drafts/vision-v1.md` with a note on what changed and why, and verify the draft is present and listed in the index
- [ ] 2.3 Review the vision against `documentation/product-vision` and verify it names a real competitive alternative, enumerates no features, and answers what, who, and why on its own

## 3. Personas

- [ ] 3.1 Write `docs/personas.md` with four personas — the multi-account multi-currency primary user, the single-bank simplicity anchor, the credential-averse household budgeter, and the irregular-income earner — and verify each is two to three paragraphs
- [ ] 3.2 Verify every persona covers personalization, job, education, and relevance, and that no persona states goals, per `documentation/personas`
- [ ] 3.3 Label each persona with its grounding, and verify the primary persona cites the behaviour documented in `Inversiones.xlsx` and the stated account topology rather than invented detail
- [ ] 3.4 Add the documented-omissions section naming excluded user types with a reason for each, and verify the financial advisor and bank operations exclusions are covered
- [ ] 3.5 Record alongside each persona the requirement it uniquely pulls, and verify no two personas pull only the same requirements

## 4. One-Pagers

- [ ] 4.1 Write `one-pagers/01-accounts-and-transaction-ingestion.md` covering connection, import, manual entry, and duplicate handling, and verify the bank developer-portal finding and the aggregator coverage gap appear in ASSUMPTIONS with sources and dates
- [ ] 4.2 Write `one-pagers/02-categorization-and-rules.md` covering automatic categorization and the independent category and spending-group dimensions, and verify at least one story covers tagging a charge at the time it occurs
- [ ] 4.3 Write `one-pagers/03-budgets-and-limits.md` covering per-group limits, alerts, and safe-to-spend for the month, and verify both the steady-income and irregular-income personas appear as story subjects
- [ ] 4.4 Write `one-pagers/04-dashboard-and-insights.md` covering spending charts and transaction views, and verify every chart story states what question the chart answers
- [ ] 4.5 Write `one-pagers/05-multi-currency-and-fx.md` covering two-currency handling, rate sourcing, account roles, and exclusion of transfers between the user's own accounts, and verify the central-bank and finance-ministry rate APIs are recorded in ASSUMPTIONS with sources
- [ ] 4.6 Write `one-pagers/06-security-and-data-control.md` covering authentication, encryption, consent, and revocation, and verify the credential-averse persona's constraint is stated as a positive story about control rather than a negative story
- [ ] 4.7 Write `one-pagers/07-investments-and-net-worth.md` covering manual holdings, live price lookup, the configurable fee profile, and net liquidation value, and verify the deposit, per-trade, and withdrawal fee types are all represented and that no multi-participant pooling appears
- [ ] 4.8 Assign every story a stable `<ordinal>-S<NN>` identifier and verify no identifier is duplicated across the document set
- [ ] 4.9 Verify every 1-pager carries all five required sections with the exact template headings in order, and that every PROBLEM section is one to two paragraphs of continuous prose containing no bullets or WHEN/THEN clauses
- [ ] 4.10 Verify every functional requirement uses the full story format with a persona defined in `personas.md`, and that every persona is the subject of at least one story

## 5. Sizing

- [ ] 5.1 Choose and publish the baseline anchor story with its point value in `docs/sizing.md`, and verify the anchor is one of the stories written in section 4
- [ ] 5.2 Size every story on the 1/2/3/5/8/13 scale with a written rationale naming the driving dimensions and the comparison made, and verify no story lacks a rationale
- [ ] 5.3 Split any story sized at 13 into smaller stories, assign the new stories fresh identifiers, size each independently, and verify no 13 remains
- [ ] 5.4 Add the estimate-uncertainty statement to `sizing.md` and verify it states these are first-pass relative estimates made without velocity history
- [ ] 5.5 Build the roll-up table in `sizing.md` listing every story by identifier with its size and 1-pager, and verify equally sized stories across different 1-pagers represent comparable effort

## 6. Review And Handoff

- [ ] 6.1 Review the document set against each of the six `documentation/` specs in turn and verify every requirement's scenarios are satisfied, recording any deviation found and corrected
- [ ] 6.2 Populate the implementation status table in `docs/README.md` and verify it reports every story as not started, matching the empty state of `openspec/specs/` and `openspec/changes/`
- [ ] 6.3 Verify `docs/README.md` lists every file present under `docs/` and that no listed file is missing
- [ ] 6.4 Confirm the set is ready for development by verifying each 1-pager's stories could be promoted to product capability specs, citing their identifiers, without further elicitation
