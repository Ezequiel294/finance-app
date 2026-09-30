# Product Evolution & AI PM Simulation Changelog

> **Course:** CS 3365 Software Engineering (Fall 2026)  
> **Deliverable:** Milestone 1 AI Prompt Log & Model Critique  
> **Rubric Items:** Detailed log of AI interactions, critique of model outputs, draft versions addressed.

---

## 1. Evolution Timeline & Major Pivots

```
┌───────────────────────────────┐        ┌───────────────────────────────┐
│     ITERATION 1 (Draft v1)    │        │    ITERATION 2 (Canonical)    │
├───────────────────────────────┤        ├───────────────────────────────┤
│ • Generic US FinTech Scope    │        │ • Costa Rica & Multi-Currency │
│ • Plaid / Yodlee Banking      │  ───►  │ • On-Device Notification Sync │
│ • Single Currency (USD)       │        │ • Dual Currency (USD & CRC)   │
│ • Generic Novice Persona      │        │ • Ezequiel Student Persona    │
│ • Simple Stock/Crypto Pricing │        │ • Inversiones.xlsx Fee Engine │
└───────────────────────────────┘        └───────────────────────────────┘
```

### Iteration 1 (2026-09-26): Baseline PM Exploration
* **Prompt Objective:** Explore scope, personas, and 1-pagers for a personal finance tracker using Sommerville's Chapter 3 guidelines and Moore's vision template.
* **Model Output:** Produced technically valid but generic US-centric specifications (Plaid banking, 401(k), US student loans).
* **Critique:** High structural compliance with class templates, but complete failure to address the lived reality of cross-border banking outside the US.
* **Archived Snapshot:** `docs/drafts/01-product-vision-v1-generic.md` and `docs/drafts/02-personas-v1-initial.md`.

### Iteration 2 (2026-09-28): Real-World Domain Grounding & Fee Math
* **Prompt Objective:** Ground the product in the author's real workflow: Costa Rican banking (BAC Credomatic & Banco Nacional), account isolation (USD salary vs. CRC debit card), interactive notification sorting ("University Living" vs. "Hobbies"), and the mathematical model from `Inversiones.xlsx`.
* **Model Output:** Replaced Devon with *Ezequiel Martinez*, architected on-device Android notification parsing, integrated BCCR exchange rates, and incorporated 1.55% deposit fees, trade commissions, and the $52 SWIFT wire exit deduction.
* **Critique:** Vastly superior relevance, concrete engineering trade-offs, and immediate utility for the project author.
* **Canonical Files Created:** `docs/01-product-vision.md`, `docs/02-personas.md`, `docs/03-backlog-and-sizing.md`, and `docs/epics/*.md`.

---

## 2. Critique of AI PM Simulation Performance

1. **Where the Model Excelled:**
   * **Textbook Adherence:** Accurately enforced Sommerville's four dimensions for personas while strictly rejecting "user goals".
   * **Mathematical Formalization:** Extracted complex Excel formulas from `Inversiones.xlsx` (e.g., grossed-up deposit fees, FIFO unit calculations, and SWIFT exit deductions) and converted them into software requirements.
   * **Template Integrity:** Strictly adhered to the 1-pager template from `project1.md` (Problem scenario, Assumptions, Functional stories, NFRs, and Fibonacci sizing).

2. **Where the Model Initially Failed (And How It Was Corrected):**
   * **Defaulting to US Assumptions:** Without explicit prompt grounding, the model defaulted to Plaid and US tax models. Prompting with specific regional banking institutions was required to force a realistic technical design.
   * **Abstract Scenarios:** Initial scenarios were generic. Providing concrete personal details (living away from parents, daily transfers to prevent card fraud) resulted in realistic, compelling problem statements.

---

## 3. Governance Policy for Future Milestones

In accordance with `openspec/config.yaml`:
* Minor updates (typos, markdown formatting) are edited directly in `docs/`.
* Substantial updates (architectural changes during Milestone 2 coding, new fee structures, or dropped epics) must be snapshotted to `docs/drafts/` with an updated entry in this changelog.
