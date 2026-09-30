## 1. Product Vision Authoring & Verification

- [ ] 1.1 Author `docs/01-product-vision.md` using Geoffrey Moore's *Crossing the Chasm* template and verify all six keywords (`FOR`, `WHO`, `THE`, `THAT`, `UNLIKE`, `OUR PRODUCT`) are present
- [ ] 1.2 Formulate explicit narrative answers to Sommerville's three fundamental product questions (What, Who, Why) within `docs/01-product-vision.md` and verify conceptual completeness
- [ ] 1.3 Articulate the product's strategic positioning across Sommerville's three design trade-off pairs (Simplicity/Functionality, Familiarity/Novelty, Automation/Control) and verify compliance with `specs/product-vision-standard/spec.md`

## 2. Persona Definitions Authoring & Validation

- [ ] 2.1 Author `docs/02-personas.md` defining three distinct financial archetypes (*Ezequiel Martinez*, *Priya Sharma*, *Marcus Vance*) and verify cohort size is between 3 and 5
- [ ] 2.2 Validate that every persona details all four mandatory dimensions (Personalization, Job-related, Education & Tech Skills, Relevance) in accordance with Sommerville ESP Ch 3
- [ ] 2.3 Audit all persona definitions to confirm zero inclusion of arbitrary "user goals" sections, verifying compliance with `specs/persona-definition-standard/spec.md`
- [ ] 2.4 Verify that technical literacy in each persona is explicitly defined to serve as an interface complexity constraint for Milestone 2 UI design

## 3. Core Epic 1-Pagers Authoring & Review

- [ ] 3.1 Author `docs/epics/epic-01-bank-aggregation.md` following the exact five-part `project1.md` template with a Sommerville narrative scenario for regional bank capture (BAC/BNCR) and verify section order
- [ ] 3.2 Author `docs/epics/epic-02-smart-categorization.md` with an interactive push notification scenario ("University Living" vs. "Hobbies") and verify functional story formatting
- [ ] 3.3 Author `docs/epics/epic-03-investment-tracker.md` modeling the 1.55% deposit surcharge, trade commissions, and $52 SWIFT exit fee from `Inversiones.xlsx` and verify narrative realism
- [ ] 3.4 Author `docs/epics/epic-04-dashboard-analytics.md` specifying dual-currency status cards, 60 FPS Skia charts, and privacy masking, verifying all NFRs define measurable metrics

## 4. Backlog Sizing & Milestone 2 Sequencing

- [ ] 4.1 Author `docs/03-backlog-and-sizing.md` containing a consolidated matrix of all 16 functional user stories and assign Modified Fibonacci story points (1, 2, 3, 5, 8, 13)
- [ ] 4.2 Provide an explicit written technical rationale for every assigned story point in `docs/03-backlog-and-sizing.md` justifying complexity, risk, and effort
- [ ] 4.3 Organize the 67 total story points into logical Milestone 2 development sprints (Foundations, Ingestion, Logic, Visuals) and verify sprint feasibility

## 5. Draft Archival, Evolution Logging & Submission Assembly

- [ ] 5.1 Archive initial exploration snapshots to `docs/drafts/01-product-vision-v1-generic.md` and `docs/drafts/02-personas-v1-initial.md` and verify "Evolution & Why This Changed" critique headers are populated
- [ ] 5.2 Author `docs/drafts/CHANGELOG-EVOLUTION.md` summarizing the AI PM simulation prompt iterations, model critique, and pivot rationale as required by `project1.md`
- [ ] 5.3 Configure `openspec/config.yaml` to enforce documentation rules, draft snapshot policies, and pre-implementation coding consultation protocols
- [ ] 5.4 Perform final verification of all documents in `docs/` against the CS 3365 rubric in `project1.md` to ensure full readiness for physical submission on October 1
