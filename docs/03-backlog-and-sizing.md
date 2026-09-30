# Requirements Sizing & Backlog Matrix

> **Course:** CS 3365 Software Engineering (Fall 2026) — Milestone 1 Deliverable  
> **Methodology:** Ian Sommerville, *Engineering Software Products* (Chapter 3) & Scrum Backlog Sizing

---

## 1. Sizing Metric & Estimation Protocol

To estimate effort across all functional requirements, the engineering team selected the **Modified Fibonacci Sequence (1, 2, 3, 5, 8, 13)** as our story point metric. 

### Why Story Points over Hours?
In agile software product development (Sommerville Ch 3), sizing by hours creates false precision during early discovery. Story points measure **relative effort**, derived from three distinct dimensions:
$$\text{Story Points} = \text{Technical Complexity} \times \text{Domain Uncertainty} \times \text{Implementation Effort}$$

* **1 Point:** Trivial change, isolated UI toggle or static styling adjustment with zero risk (e.g., privacy masking toggle).
* **2 Points:** Simple CRUD operation, database flag modification, or basic utility function.
* **3 Points:** Standard feature implementation with well-understood requirements, clear interfaces, and predictable testing paths (e.g., transaction split modal).
* **5 Points:** Moderate complexity involving cross-cutting concerns, external API integration, custom predicate evaluation, or state synchronization.
* **8 Points:** High complexity or architectural risk, such as low-level native OS bridging, background service daemons, or hardware-accelerated gesture math.
* **13 Points:** Complex epic requiring decomposition before sprint execution (none retained in our baseline backlog).

---

## 2. Consolidated Backlog Matrix

| Epic | Story ID | Functional Story Summary | Sizing (Points) | Primary Rationale |
| :--- | :--- | :--- | :---: | :--- |
| **Epic 1: Bank Aggregation** | E1-S1 | Local Push/SMS Notification Listener Bridge | **8** | Native Android background listener, OS intents, BAC/BNCR regex |
| | E1-S2 | Multi-Currency Engine & BCCR Exchange Oracle | **5** | Central bank feed sync, currency state store, exchange math |
| | E1-S3 | Intra-Account Transfer Matching Rule | **3** | Algorithmic debit/credit pairing across currencies |
| | E1-S4 | Segregated BNCR "Sobres" Vault Views | **2** | Relational schema vault tag and isolated UI cards |
| **Epic 2: Categorization & Budgets** | E2-S1 | Actionable Interactive Push Notifications | **5** | Native notification action delegates, background state updates |
| | E2-S2 | University Living Burn-Rate Progress Card | **3** | Date-math calculations, budget pace indicators, color states |
| | E2-S3 | Automated Merchant Rule Predicate Engine | **5** | Predicate logic evaluator, regex filtering, priority ordering |
| | E2-S4 | Transaction Split Editor with Validation | **3** | Relational parent-child split records and zero-remainder checks |
| **Epic 3: Multi-Asset & Net Liquidation** | E3-S1 | Contribution (Aporte) Logging with Fee Math | **3** | Form UI with 1.55% deposit + trade fee calculations |
| | E3-S2 | Real-Time Market Price Feed (VOO & BTC) | **5** | Public market APIs, WebSocket / polling, rate-limit backoffs |
| | E3-S3 | Net Liquidation Value & SWIFT Wire Cost Engine | **3** | Exact formulas from `Inversiones.xlsx`, fixed-point decimal math |
| | E3-S4 | `Inversiones.xlsx` Batch File Importer | **5** | Spreadsheet parsing, validation preview, batch SQLite insertion |
| **Epic 4: Dashboard & Analytics** | E4-S1 | Dual-Currency Summary Header | **3** | Responsive multi-column layout, currency formatting |
| | E4-S2 | Hardware-Accelerated Scrubbable Charts | **8** | React Native Skia, gesture handlers, 60 FPS mobile/web canvas |
| | E4-S3 | Asset Allocation Donut Chart with Drill-Down | **5** | Skia path animation, coordinate hit-testing, selection modal |
| | E4-S4 | One-Tap Privacy Shield | **1** | Global UI context toggle, masked value rendering |
| **Total Story Points** | | **16 Fully Specified User Stories** | **67** | **Ready for Milestone 2 Sprint Planning** |

---

## 3. Sprint Sequencing for Milestone 2

The 67 story points are divided into logical engineering sprints:
* **Sprint 1 (Foundations & Schema - 18 pts):** E4-S1, E4-S4, E1-S2, E1-S4, E2-S2, E3-S1. (Establishes local SQLite schemas, multi-currency models, and UI cards).
* **Sprint 2 (Ingestion & Notifications - 21 pts):** E1-S1, E1-S3, E2-S1, E3-S2. (Builds native background listeners, push prompts, and live price feeds).
* **Sprint 3 (Deep Logic & Mathematics - 16 pts):** E2-S3, E2-S4, E3-S3, E3-S4. (Rules engine, split editor, Excel batch import, and SWIFT exit fee liquidation math).
* **Sprint 4 (High-Performance Visuals & Polish - 12 pts):** E4-S2, E4-S3. (React Native Skia dynamic charts and gesture scrubbing).
