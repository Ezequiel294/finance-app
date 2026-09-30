# User Personas

> **Methodological Source:** Ian Sommerville, *Engineering Software Products* (Chapter 3, Section 3).  
> **Key Methodological Principle:** In strict compliance with Sommerville's findings, **these personas deliberately omit formal "user goals" sections**. Sommerville explicitly rejects "user goals" as impossible to pin down and unhelpful for software engineers. Instead, each persona details their **Personalization**, **Job-related context**, **Education & Technical Skills**, and concrete **Relevance** to the product.

```
                  ┌──────────────────────────────────────────────┐
                  │              APEXFINANCE PERSONAS            │
                  └──────────────────────┬───────────────────────┘
            ┌────────────────────────────┼───────────────────────────┐
            ▼                            ▼                           ▼
   ┌──────────────────┐        ┌──────────────────┐        ┌──────────────────┐
   │  Ezequiel M.     │        │  Priya Sharma    │        │  Marcus Vance    │
   │  "Student/Builder│        │  "Multi-Asset"   │        │  "Power User"    │
   │  Age: 22         │        │  Age: 38         │        │  Age: 31         │
   │  Dual Currency   │        │  Corporate Exec  │        │  SRE / Privacy   │
   │  BAC & BNCR User │        │  Equities & 401k │        │  Automations     │
   └──────────────────┘        └──────────────────┘        └──────────────────┘
```

---

## Persona 1: Ezequiel Martinez — The Independent Student & Cross-Border Builder (Primary Persona)

* **Personalization:** Ezequiel is a 22-year-old Software Engineering student living independently near his university in San José, Costa Rica. Living away from his family home, he manages his own rent, groceries, study supplies, and personal lifestyle. He is disciplined, financially cautious, and dedicated to building long-term investments early in his career.
* **Job-Related:** Works as a software engineering intern and part-time tech contractor. He receives his compensation in US Dollars deposited into a BAC Credomatic USD savings account. His everyday living expenses (groceries, transport, university supplies) are transacted exclusively in Costa Rican Colones (CRC).
* **Education & Technical Skills:** Fourth-year Software Engineering undergraduate. Highly tech-literate, understands APIs, databases, and financial math. Proficient with mobile apps, keyboard shortcuts, and complex Excel formulas, but frustrated by tools that require repetitive manual maintenance.
* **Relevance to Product:** Ezequiel practices strict account isolation for security: he keeps long-term emergency reserves locked in Banco Nacional (BNCR) "sobres" where he won't be tempted to touch them. His primary salary sits in a BAC USD account, but his debit card is linked only to a BAC CRC account—which he manually tops up daily with just enough money for that day's expenses to protect against card skimming and fraud. He also invests in the S&P 500 (VOO) and Bitcoin (BTC), and maintains an Excel sheet ([`Inversiones.xlsx`](file:///Users/ezequiel/Library/CloudStorage/ProtonDrive-ezequielbuckmartinez@proton.me-folder/TTU/Term%208/Software%20Engineering/Project%201/finance-app/Inversiones.xlsx)) to track deposits, platform fees (1.55%), broker commissions ($0.15 vs 1%), and exit SWIFT wire fees ($52). He needs an app that automates this entire pipeline, handles CRC/USD conversions natively, prompts him to categorize expenses between "University Living" and "Hobbies", and shows him his exact liquidated cash position.

---

## Persona 2: Priya Sharma — The High-Income Multi-Asset Corporate Professional

* **Personalization:** Priya is a 38-year-old Corporate Strategy Director living in Chicago. She manages dual executive incomes, a family mortgage, college funds, and multiple taxable brokerage accounts.
* **Job-Related:** Leads strategic acquisitions and business planning for a consumer goods corporation. Her days are filled with financial projections and executive decks. She needs high-level executive summaries on her iPad and MacBook.
* **Education & Technical Skills:** MBA in Finance and B.A. in Economics. While not a programmer, she has high digital literacy and regularly uses enterprise platforms (Salesforce, Bloomberg Terminal, Tableau). She expects intuitive, professional-grade visual reporting.
* **Relevance to Product:** Priya has traditional investment accounts (Schwab, Morgan Stanley), employer equity, and crypto holdings on Coinbase. Her primary frustration is calculating true total net worth and dynamic monthly cash flow: money moves between executive bonuses, capital calls, and tax reserves. She requires a responsive, high-fidelity tablet and desktop web dashboard that aggregates all asset classes, adjusts for market price fluctuations in real time, and produces clean visual spending reports.

---

## Persona 3: Marcus Vance — The Privacy-First Systems Reliability Engineer

* **Personalization:** Marcus is a 31-year-old Senior SRE living in Austin, Texas. He is an extreme privacy and security advocate who runs his own home server and refuses to use cloud apps that harvest transaction data for targeted loan ads.
* **Job-Related:** Manages high-throughput distributed cloud infrastructure and alerting systems. His workdays involve monitoring dashboards, configuring alerting pipelines, and writing automation scripts.
* **Education & Technical Skills:** B.S. in Computer Science. An advanced power user who uses hardware 2FA keys, command-line utilities, and custom regex rules.
* **Relevance to Product:** Marcus has multiple credit cards for travel point optimization and self-custodied crypto cold wallets. He demands local-first encrypted storage, custom merchant regex matching rules, and the ability to link financial feeds without leaking credentials or transaction histories to third-party ad networks.
