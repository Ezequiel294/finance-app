# Epic 3: Real-Time Multi-Asset Portfolio & Net Liquidation Engine

> **Template Source:** `project1.md` 1-Pager Template  
> **Methodological Source:** Ian Sommerville, *Engineering Software Products* (Chapter 3)  
> **Domain Model:** Validated by [`Inversiones.xlsx`](file:///Users/ezequiel/Library/CloudStorage/ProtonDrive-ezequielbuckmartinez@proton.me-folder/TTU/Term%208/Software%20Engineering/Project%201/finance-app/Inversiones.xlsx)

---

### PROBLEM

Ezequiel Martinez invests periodically in the S&P 500 (via the VOO ETF) and Bitcoin (BTC), tracking his portfolio through an intricate Excel spreadsheet ([`Inversiones.xlsx`](file:///Users/ezequiel/Library/CloudStorage/ProtonDrive-ezequielbuckmartinez@proton.me-folder/TTU/Term%208/Software%20Engineering/Project%201/finance-app/Inversiones.xlsx)). However, calculating how much money he *actually owns* right now is painful. Every contribution is subject to a 1.55% platform deposit fee, stock purchases carry a fixed $0.15 fee, and Bitcoin purchases incur a 1.0% variable fee. Furthermore, bringing his money back into his Costa Rican bank account incurs an estimated $52 international SWIFT wire deduction ($20 broker fee + $17 intermediary bank fee + $15 local receiving bank fee). When he opens regular investment tracking apps, they display an inflated gross balance that ignores these real-world fees. To know his true liquidated cash position or log monthly contributions ("aportes"), he has to sit down at his computer and manually update his Excel formulas.

To solve this, ApexFinance integrates the mathematical model from [`Inversiones.xlsx`](file:///Users/ezequiel/Library/CloudStorage/ProtonDrive-ezequielbuckmartinez@proton.me-folder/TTU/Term%208/Software%20Engineering/Project%201/finance-app/Inversiones.xlsx) into a streamlined mobile and web portfolio engine. Asset holdings and periodic contributions can be entered manually in seconds or imported from Excel. The system fetches live market prices for VOO and BTC in real time via public financial APIs. Using configurable fee parameters, the engine automatically calculates Total Invested, Total Ingress Fees (1.55%), Asset Commissions, and deducts the $52 SWIFT exit fee, presenting the user with their true **Net Liquidation Value** ("What you would actually deposit in your bank if you sold everything right now") alongside true net profit percentages.

---

### ASSUMPTIONS

* Asset quantities and contribution events (Aportes) can be recorded manually; direct broker API integration (e.g. Interactive Brokers) is an optional future convenience, not a blocker.
* Public market APIs (e.g., Yahoo Finance, Google Finance, CoinGecko) provide free, reliable real-time and delayed market quotes for VOO and BTC/USD.
* Configurable fee defaults match user reality: 1.55% deposit surcharge, $0.15 fixed stock fee, 1.0% crypto fee, and $52 flat SWIFT repatriation wire fee.
* Multi-investor pooling (as modeled in `Inversiones.xlsx` with Ezequiel, Brian, and Andrea) can be represented via distinct sub-portfolios or individual user filters.

---

### FUNCTIONAL REQUIREMENTS

* **As a** user like Ezequiel, **I want to** log periodic contributions ("aportes") of money invested into VOO or Bitcoin **so that I can** record my purchase date, share price, and units without opening Excel.
  * *Detail A:* Input form captures Date, Asset (VOO or BTC), Total Dollars Deposited, and Share/Coin Units purchased.
  * *Detail B:* System automatically calculates and records the 1.55% deposit commission and transaction fee based on asset type ($0.15 for VOO, 1% for BTC).

* **As a** user like Ezequiel, **I want to** fetch real-time market prices for VOO and BTC **in order to** view live asset valuations without manual price lookups.
  * *Detail A:* Equity prices fetched from financial market APIs during trading hours; BTC prices refreshed via CoinGecko/Coinbase APIs every 60 seconds.
  * *Detail B:* System displays 24-hour price change and percentage trend badges.

* **As a** user like Ezequiel, **I want to** view my "Net Liquidation Value" including the $52 SWIFT wire exit deduction **so that I know** the exact cash payout I would receive in my bank if I liquidated today.
  * *Detail A:* Calculation: `Liquid Cash = (VOO_units * Price_VOO + BTC_units * Price_BTC) - Total_Invested_Cost - SWIFT_Exit_Fees ($52)`.
  * *Detail B:* Displays both Gross Market Value and True Net Cashout with fee deduction transparently itemized.

* **As a** user like Ezequiel, **I want to** import my existing historical contributions from `Inversiones.xlsx` with a single file upload **so that I can** migrate my multi-year investment history seamlessly.
  * *Detail A:* Client parses `.xlsx` or `.csv` structure matching the `Aportes` sheet columns (Persona, Fecha, Precio, Acciones, Invertido, Comision).
  * *Detail B:* Validation preview displays parsed records before committing them to the local database.

---

### NON-FUNCTIONAL REQUIREMENTS

* **Calculation Precision:** All currency arithmetic must use fixed-point decimal math (e.g., `decimal.js`) to 8 decimal places for Bitcoin and 2 decimal places for fiat, eliminating IEEE 754 floating-point rounding errors.
* **Market Data SLA:** Crypto market prices refreshed within 60 seconds of client load; equity quotes delayed by no more than 15 minutes during standard exchange operating hours.
* **Offline Valuation:** When offline, the app computes portfolio metrics using the last recorded closing prices and displays an offline indicator badge.

---

### REQUIREMENTS SIZING

*Selected Metric: Modified Fibonacci Story Points (1, 2, 3, 5, 8, 13).*

* **Story 1 (Contribution / Aporte Logging with Automated Fee Math):** **3 Points**  
  *Rationale:* Form UI with real-time formula computation mirroring `Inversiones.xlsx` (1.55% deposit + $0.15 or 1% fee).
* **Story 2 (Real-Time Market Price Feed Integration - VOO & BTC):** **5 Points**  
  *Rationale:* Requires building resilient API polling/WebSocket client connectors for Yahoo Finance and CoinGecko with error handling and rate-limit backoffs.
* **Story 3 (Net Liquidation Value & SWIFT Exit Cost Engine):** **3 Points**  
  *Rationale:* Implementation of exact financial formulas from `Inversiones.xlsx` with fixed-point decimal arithmetic and UI itemization cards.
* **Story 4 (Inversiones.xlsx Batch File Import):** **5 Points**  
  *Rationale:* Involves client-side spreadsheet parsing (`xlsx` library in JS), schema validation, error highlighting for malformed rows, and batch database insertions.
