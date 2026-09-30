# Epic 2: Smart Contextual Categorization & University Expense Grouping

> **Template Source:** `project1.md` 1-Pager Template  
> **Methodological Source:** Ian Sommerville, *Engineering Software Products* (Chapter 3)

---

### PROBLEM

Living independently near campus, Ezequiel has a fixed monthly budget allocated for essential living expenses (apartment rent, groceries, electricity, internet, and university materials). However, his daily spending frequently overlaps with social outings, coffee with friends, gaming subscriptions, and personal hobbies. In existing budgeting apps, every transaction must be categorized manually after the fact, or else everything gets lumped into generic categories. When an expense hits his card from a grocery store or convenience shop, Ezequiel cannot easily remember whether it was an essential meal supply for his university week or snacks bought during a weekend gathering. By the end of the month, his university living budget runs over because discretionary hobby expenses bled into his essential envelope.

To address this, ApexFinance introduces a contextual notification prompt. Whenever a new transaction is recorded on the BAC Colones card, the app triggers an actionable push notification directly to Ezequiel’s phone screen: *"₡12,000 charged at AM/PM. Add to University Living Essentials or Hobbies/Discretionary?"* With a single tap directly on the notification action buttons, Ezequiel categorizes the expense in under two seconds without even opening the app. For complex receipts, the app allows easy one-tap transaction splitting, while the dashboard provides a clear visual burn-rate gauge dedicated specifically to the "University Living" allowance.

---

### ASSUMPTIONS

* Modern mobile OS platforms (iOS and Android) support actionable push notifications with interactive buttons (`expo-notifications` interactive categories).
* The user defines an explicit monthly spending cap for their "University Living" group at the beginning of each billing cycle.
* Uncategorized transactions remain in a prominent "Needs Review" queue on the home dashboard until confirmed by the user.
* Repetitive charges from specific merchants (e.g., University Tuition portal or Landlord wire) can be set to bypass the prompt and auto-assign to University Essentials.

---

### FUNCTIONAL REQUIREMENTS

* **As a** user like Ezequiel, **I want to** receive an interactive push notification immediately after a charge occurs asking me to assign it to "University Living" or "Hobbies" **so that I can** keep my essential student expenses separated with a single tap.
  * *Detail A:* Notification provides quick-action buttons: `[University Living]`, `[Hobbies/Personal]`, and `[Split/Other]`.
  * *Detail B:* Tapping an action button categorizes the transaction immediately in the background and dismisses the notification.

* **As a** user like Ezequiel, **I want to** view a dedicated "University Living" budget progress card **in order to** ensure my essential survival funds last until the end of the month.
  * *Detail A:* Card displays total spent, monthly cap, remaining days in month, and a "Safe Daily Spend Pace" in Colones (₡).
  * *Detail B:* Progress indicator shifts color from green to amber if daily spend pace exceeds the planned burn rate.

* **As a** user like Marcus, **I want to** configure automated merchant assignment rules **so that I can** automatically assign predictable recurring bills without seeing a notification prompt.
  * *Detail A:* Rules interface supports conditions (e.g., "If merchant contains *Uber Eats*, assign to *Hobbies/Dining*").
  * *Detail B:* User can prioritize rules and test them against historical transactions.

* **As a** user like Priya, **I want to** split a large supermarket purchase into both essential food and home/personal care **so that I can** maintain pristine accounting accuracy.
  * *Detail A:* Split editor modal provides real-time remainder calculation ensuring total splits equal the parent charge.
  * *Detail B:* Split child items display linked under the master transaction in the history ledger.

---

### NON-FUNCTIONAL REQUIREMENTS

* **Notification Latency:** Contextual push prompts must be generated and delivered to the user's notification shade within 3 seconds of transaction ingestion.
* **UI Responsiveness:** Interactive notification button action must complete background state update and persist to local SQLite in under 200 milliseconds.
* **Battery & Resource Efficiency:** Background notification processing must consume less than 1% of battery life over a 24-hour cycle.

---

### REQUIREMENTS SIZING

*Selected Metric: Modified Fibonacci Story Points (1, 2, 3, 5, 8, 13).*

* **Story 1 (Actionable Interactive Push Notification Prompts):** **5 Points**  
  *Rationale:* Involves configuring native notification action delegates, background task execution when app is closed, and optimistic local database writes.
* **Story 2 (Dedicated University Living Burn-Rate Gauge):** **3 Points**  
  *Rationale:* Straightforward calculation logic based on elapsed days vs budget ceiling, built into a responsive React Native progress card.
* **Story 3 (Automated Merchant Rule Predicate Engine):** **5 Points**  
  *Rationale:* Requires building a rules evaluator (regex, string-matching, threshold conditions) and managing rule priority conflicts.
* **Story 4 (Transaction Split Editor with Validation):** **3 Points**  
  *Rationale:* Front-end modal design with arithmetic zero-remainder validation and relational database child-record storage.
