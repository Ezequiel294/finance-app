# Epic 1: Multi-Currency Banking Aggregation & Local Transaction Capture Engine

> **Template Source:** `project1.md` 1-Pager Template  
> **Methodological Source:** Ian Sommerville, *Engineering Software Products* (Chapter 3)

---

### PROBLEM

Ezequiel Martinez is a university student living independently who receives his internship salary in US Dollars into a BAC Credomatic USD account. For security, his physical debit card is tied exclusively to a separate BAC Colones (CRC) account, which he funds every morning by transferring only the money he intends to spend that day, preventing card skimmers from accessing his main salary. Additionally, he keeps his untouchable emergency savings locked in "sobres" inside Banco Nacional (BNCR). In his current setup with apps like *Wallet* or manual spreadsheets, transactions in Costa Rica fail to sync automatically due to lack of local open-banking standards, and currency conversions between CRC and USD distort his balances. Every Sunday night, Ezequiel is forced to log into both banking portals, calculate daily exchange rate differences, and manually record each purchase line by line into Excel.

To solve this, the aggregation engine introduces a hybrid ingestion architecture designed for regional banking environments. On mobile devices, a native notification and SMS parsing bridge intercepts real-time transaction authorizations sent by BAC Credomatic and BNCR, extracting the merchant name, currency (CRC or USD), and timestamp instantly without requiring invasive login credentials. For structured updates, the system integrates with regional open-banking aggregators (Prometeo API) and supports one-click BAC statement CSV imports. An integrated currency oracle fetches daily official exchange rates from the Central Bank of Costa Rica (BCCR), allowing transfers between USD salary accounts and the CRC debit card to be automatically classified as internal transfers rather than phantom expenses.

---

### ASSUMPTIONS

* In Costa Rica, BAC Credomatic and BNCR push instant notifications or SMS alerts for all debit card purchases, containing consistent transaction text patterns.
* The device operating system (Android native bridge via React Native Headless JS) allows local notification listening permissions granted explicitly by the user.
* Central Bank of Costa Rica (BCCR) provides a public web service or scrapable daily indicator feed for official USD/CRC reference buy/sell exchange rates.
* Intra-account transfers (e.g., transferring $20 USD from BAC USD to CRC debit card) are detected by matching identical timestamps and converted amounts, preventing them from being counted as double expenses.
* User bank credentials are never stored by the app; external data ingestion relies strictly on local push parsing, certified regional APIs, or local file uploads.

---

### FUNCTIONAL REQUIREMENTS

* **As a** user like Ezequiel, **I want to** automatically capture BAC Credomatic debit card transactions via on-device notification parsing **so that I can** see my everyday expenses recorded in real time without manual entry.
  * *Detail A:* App listens for BAC notification strings (e.g., *"Compra aprobada por ₡8,500 en Automercado"*), extracting amount, currency, and vendor.
  * *Detail B:* Successfully parsed notifications trigger a subtle local confirmation and update the local CRC transaction ledger instantly.

* **As a** user like Ezequiel, **I want to** track accounts in both Costa Rican Colones (CRC) and US Dollars (USD) with live exchange rate normalization **in order to** view my total cash balance accurately without manual currency math.
  * *Detail A:* System integrates the BCCR daily exchange rate feed and updates reference rates every morning at 6:00 AM.
  * *Detail B:* User can toggle the dashboard view between "Native Currency", "All in CRC (₡)", or "All in USD ($)".

* **As a** user like Ezequiel, **I want to** mark transfers from my BAC USD account to my CRC card account as "Internal Transfers" **so that I can** avoid skewing my monthly expense reports with phantom spending.
  * *Detail A:* Transfer detection rule automatically pairs an outflow in USD with an equivalent inflow in CRC occurring within a 15-minute window.
  * *Detail B:* Internal transfers are excluded from monthly budget consumption calculations.

* **As a** user like Ezequiel, **I want to** register Banco Nacional "sobres" as segregated reserve accounts **so that I can** protect my emergency savings from being factored into my daily spendable allowance.
  * *Detail A:* "Sobres" accounts are explicitly tagged as "Locked Savings" and displayed in a separate dashboard card.
  * *Detail B:* Visual indicator highlights whether the target reserve goal for each sobre has been reached.

---

### NON-FUNCTIONAL REQUIREMENTS

* **Data Privacy & Security:** Zero plaintext cloud storage of banking credentials. Notification parsing occurs entirely on-device; intercepted notification strings are never sent to external servers.
* **Parsing Performance:** On-device notification regex tokenization and transaction generation must execute in under 100 milliseconds upon receipt.
* **Exchange Rate Reliability:** If the BCCR API is unreachable, the system must gracefully fall back to the last cached exchange rate and display a "Rate cached from [Date]" indicator.

---

### REQUIREMENTS SIZING

*Selected Metric: Modified Fibonacci Story Points (1, 2, 3, 5, 8, 13) reflecting technical complexity, integration volatility, and testing overhead.*

* **Story 1 (Local Push/SMS Notification Listener Bridge):** **8 Points**  
  *Rationale:* High technical complexity. Involves building native Android Headless JS background services, managing OS permission handshakes, and writing resilient regex parsers for BAC/BNCR notification formats.
* **Story 2 (Multi-Currency Engine & BCCR Exchange Rate Oracle):** **5 Points**  
  *Rationale:* Moderate-to-high complexity. Requires building BCCR API integration, caching layers, and currency conversion math across all UI display elements.
* **Story 3 (Intra-Account Transfer Matching Rule):** **3 Points**  
  *Rationale:* Moderate effort. Involves algorithmic matching of debit/credit pairs across different currencies within a sliding time window.
* **Story 4 (Segregated BNCR "Sobres" Vault Views):** **2 Points**  
  *Rationale:* Low complexity. Relational database schema flag (`is_locked_vault`) and specialized front-end presentation cards.
