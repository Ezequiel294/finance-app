# Budgets and Limits

### PROBLEM

People paid once a month into one account, who spend from their phone in many small
amounts, often learn they have overspent by running out of money. Nothing gives them a
running sense of what is left until the balance does. The week before payday is
predictable in hindsight and invisible at the time, because the decisions that caused it
were made two weeks earlier. They don't need a report. They need to be told, while there
are still decisions to make, that the month is running short. People paid in irregular
lumps, when client invoices clear, have the opposite problem. The usual advice, dividing
monthly income into categories, fails because there is no monthly income to divide. A
good month feels like they can afford anything and a lean one feels like an emergency,
even when the two average out. They don't want a prediction of future income. They want
the money already in their account described honestly: what is committed, what is free,
and how long it lasts if nothing else arrives.

People who already budget carefully have a third problem: they can't see how they are
doing. They watch groceries by the week, rent by the month, and clothing by the year, all
at once, and every tool assumes the month is the only unit. When they do get a total,
they must work out the proportion themselves: ₡68,000 against ₡45,000 set aside is 151%,
the number that actually tells them something. No tool tells them what a year of keeping
to their budgets is worth, which is the reason they keep them. And people who share
household costs with a partner, while each spends from their own accounts, argue less
about the total than about who spent what, which neither can answer at the end of the
month.

### ASSUMPTIONS

- **Assumed.** A budget's period is a week, a calendar month, or a calendar year, chosen
  per budget. A person may run budgets of different periods at the same time over the
  same money, and no period is privileged over the others.
- **Assumed.** Budgets at different periods are independent of one another. A weekly
  grocery budget does not roll up into, or draw down from, a monthly or annual one.
- **Unverified.** Whether nested budgets — a weekly allowance drawing from a monthly
  envelope drawing from an annual one — are wanted. Nesting requires allocation and
  rollover rules and is materially larger than independent periods, so it is excluded
  until asked for. Settled by asking people who budget over several periods at once.
- **Assumed.** A week runs Monday to Sunday. Weeks do not divide evenly into months or
  years, so a weekly budget's periods are counted from its start date rather than aligned
  to month boundaries.
- **Assumed.** The year-end saving figure projects *adherence*, not income: it assumes the
  person spends exactly to budget for the periods remaining, and adds the surplus or deficit
  already accumulated. It is a statement of what the budgets are worth if kept, not a
  forecast of what will happen.
- **Assumed.** Committed costs — rent, subscriptions, recurring transfers — can be
  identified from repeating transactions, and the user can confirm or correct the list
  rather than entering it from scratch.
- **Assumed.** Safe-to-spend is computed only from money that has actually arrived. No
  story here projects future income, and expected invoices are excluded from the figure
  even when the user knows about them.
- **Assumed.** Two people sharing a household budget each hold their own accounts, and
  sharing means sharing the budget and the transactions attributed to it, not access to
  each other's accounts.
- **Unverified.** That an alert delivered before an overspend actually changes behaviour
  rather than being dismissed like every other notification. Settled by observing whether
  users who receive them end periods within their limits more often than those who do not.
- **Assumed.** Limits are advisory. Nothing in the product blocks or declines a
  transaction, and no story here implies it could.

### STORIES

* **03-S01** — **When** I am paid once a month and spend in many small amounts with no
  running sense of what is left, **I want to** be warned that I am running down the money
  I had for the month, **so that** I can change what I do while it still makes a
  difference.
  * The warning arrives on crossing a proportion of the limit the person sets, not on
    exceeding it
  * It states how much is left and how many days remain in the period
  * Warnings can be silenced per budget without switching off the budget itself

* **03-S02** — **When** I set money aside for different purposes, such as living costs and
  hobbies, **I want to** set a separate limit for each spending group, **so that** I can
  keep my university costs and my hobbies from being measured against one another.
  * Each group carries its own limit and period
  * A group with no limit still accumulates a total and is simply not compared against one
  * Progress against every limit is visible in one view

* **03-S03** — **When** my income arrives in irregular lumps, **I want to** see how much I
  can safely spend this period, **so that** I can stop guessing in the weeks between
  client payments.
  * The figure is derived from money that has arrived, less committed costs, and never
    from anticipated income
  * The product shows what it subtracted to reach the figure
  * The figure updates when a payment arrives or a commitment changes

* **03-S04** — **When** I don't know when my next payment will arrive, **I want to** see
  how long my current money lasts at my current rate of spending, **so that** I can judge
  how lean a month I am actually in.
  * The projection is stated as a date or a number of weeks, with the spending rate it
    assumes
  * The rate used is visible and can be based on a period the person chooses
  * The projection is presented as a consequence of current behaviour, not a prediction of
    the person's income

* **03-S05** — **When** I share household costs with a partner but each of us spends from
  our own accounts, **I want to** share a household budget with my partner, **so that** I
  can see one agreed set of figures instead of each of us keeping our own.
  * Both people see the same budget, limits, and attributed transactions
  * Each transaction attributed to the household budget shows who spent it
  * Sharing a budget gives neither person access to the other's accounts or to
    transactions outside the shared budget

  > **Split.** Replaced by **03-S07**, **03-S08**, and **03-S09** below. Kept here because
  > it states the need those stories exist to serve.

* **03-S06** — **When** part of my money is already promised to rent, subscriptions, and
  other regular costs, **I want to** confirm which of my recurring costs are commitments,
  **so that** I can have them excluded from what I think is free to spend.
  * Repeating transactions are proposed as candidate commitments for the person to confirm
  * A confirmed commitment is subtracted from safe-to-spend for its period
  * A commitment can be added by hand for something that has not recurred yet

* **03-S07** — **When** I want to budget household costs together with someone who spends
  from their own accounts, **I want to** invite my partner to a budget, **so that** I can
  have us both working from the same agreed figures.
  * An invitation goes to a person the inviter names and takes effect once they accept
  * Accepting grants sight of the budget, its limits, and the transactions attributed to it
  * Neither person gains sight of the other's accounts or of anything outside that budget

* **03-S08** — **When** we both pay toward a shared budget and disagree about who spent
  what, **I want to** see who paid for each transaction in our shared budget, **so that**
  I can settle what each of us actually contributed.
  * Every attributed transaction shows which participant it came from
  * Totals can be read per participant as well as for the budget as a whole
  * Attribution follows the originating account rather than being entered by hand

* **03-S09** — **When** I have shared a budget with someone, **I want to** end sharing
  whenever I decide to, **so that** I can stay in control of what my partner can see.
  * Either participant can end sharing, and it takes effect immediately
  * The person ending sharing is told what the other person will stop seeing before they
    confirm
  * After ending, neither participant can read data the other contributed

* **03-S10** — **When** some of my spending only makes sense over a week and some only
  over a year, **I want to** set a budget over a week, a month, or a year, **so that** I
  can watch the things that vary weekly apart from the ones only a year makes sense of.
  * A budget's period is chosen when it is created and can be changed afterwards
  * Budgets of different periods run at the same time over the same transactions
  * A weekly budget counts its periods from its own start date rather than from month
    boundaries

* **03-S11** — **When** I check how my budgets are going, **I want to** see what
  proportion of each budget I have used, including when I have gone past it, **so that**
  I can tell at a glance how far over or under I am rather than comparing two figures
  myself.
  * The proportion is stated as a percentage wherever a budget appears
  * A budget exceeded reads above 100% — 151%, not a full bar — and the amount over is
    shown alongside it
  * The underlying spent and budgeted amounts remain visible next to the proportion

* **03-S12** — **When** I keep to my budgets in order to save by the end of the year,
  **I want to** see what I would have saved by the end of the year if I stay inside my
  budgets, **so that** I can tell what keeping to them is actually worth.
  * The figure assumes spending exactly to budget for the periods remaining, and includes
    the surplus or deficit already accumulated
  * It states plainly that it assumes adherence rather than predicting the person's
    spending
  * The person can see the periods and budgets it was built from

### NON-FUNCTIONAL REQUIREMENTS

- **Warning timeliness.** A threshold warning is delivered within 15 minutes of the
  transaction that crosses it, since a warning after the fact is a report.
- **Warning restraint.** At most one threshold warning per budget per period, unless the
  user opts into more. An alert people learn to dismiss has negative value.
- **Recalculation performance.** Safe-to-spend and limit progress recompute within 1
  second of a transaction changing, across 5,000 transactions in the period.
- **Proportion presentation.** A budget's consumption is shown as a percentage rounded to
  a whole number, with no upper bound on the value displayed. Exceeding a budget is never
  represented only by a filled bar or a colour change.
- **Multi-period performance.** Progress for 20 budgets across mixed weekly, monthly, and
  annual periods recomputes within 1 second of a transaction changing.
- **Sharing isolation.** A person invited to a shared budget can read only the budget,
  its limits, and transactions explicitly attributed to it. Account balances and
  unattributed transactions are never exposed by sharing.
- **Sharing revocability.** Either participant can end sharing at any time, taking effect
  immediately; afterwards neither can read data created by the other.
- **Transparency of derivation.** Every derived figure — safe-to-spend, runway, progress —
  can be expanded to show the inputs it was computed from. No number appears without a
  way to see where it came from.
- **Advisory only.** No limit, warning, or projection blocks, delays, or modifies any
  transaction.
