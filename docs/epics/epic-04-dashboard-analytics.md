# Epic 4: Cross-Platform Interactive Dashboard & Dual-Currency Analytics

> **Template Source:** `project1.md` 1-Pager Template  
> **Methodological Source:** Ian Sommerville, *Engineering Software Products* (Chapter 3)

---

### PROBLEM

Ezequiel studies on a MacBook, codes on a desktop workstation, and manages daily life on his mobile phone. Existing apps force him into cramped mobile-only layouts that cannot be viewed on a desktop browser, or web dashboards that look like stretched-out mobile phone screens. Furthermore, because his finances span two distinct currencies (Colones for local life, Dollars for salary and investments), existing dashboards force everything into a single currency using inaccurate internal rates, making his CRC checking account look artificially unstable. He needs a responsive, hardware-accelerated dashboard that runs natively across mobile and desktop web, clearly separates his CRC daily spend from his USD net worth, and renders dynamic spending trends and asset distribution charts with 60 FPS fluidity.

To solve this, ApexFinance delivers a cross-platform presentation layer built with React Native for Web and Expo Router. The dashboard features a multi-currency header showing live BAC CRC spendable balance, BAC USD salary reserves, BNCR savings "sobres", and Net Liquidated Investments side by side. Dynamic charts powered by React Native Skia allow smooth gesture scrubbing across monthly spending trends and asset allocation rings. On desktop browsers, the interface expands into an adaptive multi-column command center, while on mobile devices it condenses into a clean, swipeable feed optimized for quick single-handed checks.

---

### ASSUMPTIONS

* Single codebase runs across iOS, Android, and Desktop Web via React Native for Web and Expo Router.
* Visual components dynamically format currency strings according to locale: Costa Rican Colones (`₡12,500`) and US Dollars (`$450.00`).
* Local-first database (WatermelonDB or OP-SQLite) ensures instantaneous screen loads and full offline accessibility.
* Dark mode is supported out of the box to accommodate evening student study sessions.

---

### FUNCTIONAL REQUIREMENTS

* **As a** user like Ezequiel, **I want to** view a dual-currency summary header displaying my daily CRC spendable funds, USD bank reserves, and Net Investment value **so that I can** assess my complete financial standing at a glance.
  * *Detail A:* Top cards show: `Spendable Today (CRC ₡)`, `Protected Salary (USD $)`, `BNCR Sobres (CRC/USD)`, and `Liquid Investments (USD $)`.
  * *Detail B:* Currency amounts are rendered in distinct visual badges with clear currency symbols.

* **As a** user like Devon or Ezequiel, **I want to** scrub across dynamic spending charts to see day-by-day cash outflows **in order to** identify which days of the week have the highest expenditure.
  * *Detail A:* Touch and mouse hover scrubbing displays date, total spend, and top merchant for that specific day.
  * *Detail B:* Segmented filters allow toggling between 7-Day, 30-Day, Month-to-Date, and Custom Date Ranges.

* **As a** user like Priya or Ezequiel, **I want to** view an interactive asset allocation donut chart showing the balance between Cash, S&P 500, and Bitcoin **so that I can** ensure my portfolio doesn't become overly concentrated in crypto.
  * *Detail A:* Interactive Skia donut chart with animated slice expand on selection.
  * *Detail B:* Tapping an asset slice displays total units, average cost basis, and current liquidated profit.

* **As a** user like Ezequiel, **I want to** toggle a "Privacy Mode" with one tap **so that I can** check my budget in public or around university classmates without displaying sensitive dollar balances.
  * *Detail A:* Header eye icon toggles all financial figures to masked state (`••••••`).
  * *Detail B:* Masking preference is remembered across app sessions.

---

### NON-FUNCTIONAL REQUIREMENTS

* **Rendering Performance:** Chart interactions and screen navigation must maintain 60 FPS on mobile and up to 120 FPS on high-refresh desktop displays.
* **Initial Page Load:** Dashboard initial contentful paint on web must be achieved in under 1.2 seconds; mobile app cold start to interactive state in under 1.0 second.
* **Cross-Platform Parity:** 100% feature and visual parity between Mobile (iOS/Android) and Web dashboard interfaces.

---

### REQUIREMENTS SIZING

*Selected Metric: Modified Fibonacci Story Points (1, 2, 3, 5, 8, 13).*

* **Story 1 (Dual-Currency Adaptive Summary Header):** **3 Points**  
  *Rationale:* Cross-platform responsive card layout with multi-currency string formatting and real-time state binding.
* **Story 2 (Interactive Skia Hardware-Accelerated Trend Charts):** **8 Points**  
  *Rationale:* High UI complexity. Configuring `@shopify/react-native-skia` gesture responders, smooth spline interpolations, and web canvas fallbacks.
* **Story 3 (Asset Allocation Donut Chart with Drill-Down):** **5 Points**  
  *Rationale:* Interactive SVG/Skia path animation, coordinate hit-testing, and dynamic selection state linking.
* **Story 4 (One-Tap Global Privacy Shield):** **1 Point**  
  *Rationale:* Low complexity. React Context state toggle replacing text children with masked characters.
