# [ARCHIVED DRAFT v1] - Product Overview & Vision

> **Snapshot Date:** 2026-09-26  
> **Status:** Superseded by canonical `docs/01-product-vision.md`  
> **Author/Model:** PM Simulator (Initial Exploration)  
> **Purpose:** Document early draft and AI interaction iteration for CS 3365 rubric compliance.

---

## Evolution & Why This Version Changed

### 1. What was deficient in this initial version?
* **Assumed standard US banking infrastructure:** Relied on US Plaid/MX APIs, which completely fail to connect with Costa Rican financial institutions such as BAC Credomatic and Banco Nacional.
* **Single-currency blind spot:** Treated all funds as US Dollars, ignoring the operational reality of earning in USD while paying daily expenses through a Colones (CRC) debit card.
* **Omitted real-world investment friction:** Modeled S&P 500 and cryptocurrency tracking as simple API balance lookups, ignoring the 1.55% platform deposit surcharge, trade commissions, and the $52 international SWIFT wire exit deduction.

### 2. What new constraints or insights prompted the change?
* Direct domain feedback and user workflow analysis revealed that managing personal finances across two Costa Rican banks requires specialized on-device notification parsing and BCCR Central Bank exchange rate integration.
* The user's actual investment spreadsheet ([`Inversiones.xlsx`](file:///Users/ezequiel/Library/CloudStorage/ProtonDrive-ezequielbuckmartinez@proton.me-folder/TTU/Term%208/Software%20Engineering/Project%201/finance-app/Inversiones.xlsx)) revealed that true portfolio tracking requires calculating **Net Liquidation Value** after deducting all ingress, transaction, and repatriation fees.

### 3. Decisions incorporated into Canonical v2 (`docs/01-product-vision.md`):
* Replaced Plaid-centric vision with a hybrid on-device notification listener architecture.
* Introduced native USD/CRC dual-currency support with BCCR reference rate normalization.
* Incorporated the exact mathematical fee formulas from `Inversiones.xlsx`.

---

*(Original Draft Content Follows Below)*

### Original Vision Statement (Draft v1)
> **FOR** digital-native working professionals and retail investors  
> **WHO** struggle to maintain an accurate, unified picture of their net worth across fragmented bank accounts, equity brokerages, and crypto wallets,  
> **THE** **ApexFinance Tracker** **IS A** cross-platform, automated personal finance intelligence dashboard  
> **THAT** synchronizes live transactions via Plaid, automates categorical spending analysis against dynamic budget limits, and provides real-time portfolio performance tracking,  
> **UNLIKE** traditional budgeting apps that monetize personal data or require manual CSV imports,  
> **OUR PRODUCT** combines zero-knowledge client-side security, sub-second interactive visualization across mobile and web, and native multi-institution API connectivity in an ad-free interface.
