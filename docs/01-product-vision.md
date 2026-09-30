# ApexFinance: Product Overview & Vision

> **Course:** CS 3365 Software Engineering (Fall 2026) — Project Milestone 1  
> **Author:** Ezequiel Martinez  
> **Methodological Source:** Ian Sommerville, *Engineering Software Products* (Chapters 1 & 3)

---

## 1. Product Opportunity & Problem Statement

In accordance with Sommerville's distinction between project-based and product-based software engineering (Chapter 1, Section 2), **ApexFinance** is driven not by an individual client's contract, but by an **opportunity**: the widespread frustration among digitally active individuals and students managing cross-border, multi-currency finances across fragmented retail banks, equity brokerages, and cryptocurrency assets.

Existing consumer budgeting tools (such as *Wallet by BudgetBakers* or US-centric platforms like Mint) fail in practical cross-border use cases:
1. **Regional Ingestion Barrier:** US aggregators (Plaid, Yodlee) do not support Latin American banking institutions such as **BAC Credomatic** or **Banco Nacional (BNCR)**.
2. **Multi-Currency Account Isolation Distortion:** Standard apps enforce single-currency views that fail to reflect the security practice of earning salary in **USD** while operating a debit card strictly bound to **CRC (Costa Rican Colones)** funded only for daily use.
3. **The Investment "Hidden Cost" Myth:** Mainstream portfolio apps display gross market balance while completely ignoring the real-world friction of international retail investing: the **1.55% platform deposit surcharge**, asset-specific purchase commissions (**$0.15 for VOO vs. 1.0% for Bitcoin**), and the flat **$52 international SWIFT wire exit deduction** required to repatriate funds into local accounts.

---

## 2. The Three Fundamental Product Questions (Sommerville Ch 1.7)

1. **What is the product you propose to develop, and what makes it different from competing products?**  
   **ApexFinance** is an automated, cross-platform personal finance intelligence and portfolio dashboard. It bridges traditional retail banking (checking, daily card spend, locked savings "sobres") with multi-asset wealth tracking (S&P 500 equities and Bitcoin) in a unified, local-first interface. Unlike legacy apps, it automates transaction ingestion via an on-device notification listener without requiring bank passwords, and computes **true net liquidation value** rather than gross paper wealth.

2. **Who are the target users and customers?**  
   Independent university students, young working professionals, and retail investors who manage money across multiple currencies, maintain isolated accounts for fraud protection, and invest periodically in stocks and crypto.

3. **Why should customers choose this product?**  
   Managing spreadsheets ([`Inversiones.xlsx`](file:///Users/ezequiel/Library/CloudStorage/ProtonDrive-ezequielbuckmartinez@proton.me-folder/TTU/Term%208/Software%20Engineering/Project%201/finance-app/Inversiones.xlsx)) requires hours of tedious weekly reconciliation. Competing mobile apps lack Costa Rican bank compatibility, fail at multi-currency budgeting, and monetize user transaction data. ApexFinance offers zero-maintenance automated tracking, real-time push categorization, and total data privacy.

---

## 3. Geoffrey Moore's Vision Template (*Crossing the Chasm*)

> **FOR** independent university students and multi-currency wealth builders  
> **WHO** are burdened by manual spreadsheet updates and let down by budgeting apps that fail with foreign banks, mishandle multi-currency accounts, and ignore real-world investment fees,  
> **THE** **ApexFinance Tracker** **IS A** cross-platform, automated financial intelligence and portfolio application  
> **THAT** synchronizes live banking transactions across regional and international accounts, automates expense classification between university essentials and discretionary spend via smart push prompts, and computes live net liquidation values for S&P 500 and Bitcoin holdings,  
> **UNLIKE** generic budgeting tools like Wallet by BudgetBakers or Mint that break outside the US and lack fee-aware investment modeling,  
> **OUR PRODUCT** provides native USD/CRC dual-currency support, regional bank connectivity, and transparent, fee-adjusted investment analytics in an ad-free, local-first interface.

---

## 4. Product Design Trade-Offs (Sommerville Ch 3.6)

* **Simplicity ↔ Functionality:** ApexFinance uses progressive disclosure. The top-level interface displays a high-level summary of "Daily Spendable (CRC)", "Protected Salary (USD)", and "Net Liquid Investments"; users can drill down into granular transaction tags, fee breakdowns, and cost-basis lots on demand.
* **Familiarity ↔ Novelty:** We preserve the familiar envelope budgeting mental model (mirroring BNCR "sobres") and traditional spreadsheet ledgers, while introducing novel interactive mobile push notifications that prompt for one-tap category assignment immediately upon card swipe.
* **Automation ↔ Control:** Automated on-device listeners capture 95%+ of incoming card transactions, while manual investment entries and one-tap categorization confirmations ensure the software never makes unauthorized financial assumptions.
