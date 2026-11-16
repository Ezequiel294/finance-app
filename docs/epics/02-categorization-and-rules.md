# Categorization and Rules

### PROBLEM

Much spending answers two questions at once, and existing tools only ask one. A ₡14,000
supermarket charge is groceries, because that is what it was. It may also belong to money
set aside for a particular purpose, such as living away from home, which is a different
question with a different budget behind it. Some food spending belongs to one purpose and
some to a hobby, and a tracker that allows one label forces people to throw one of those
facts away. People who keep a spreadsheet solve this with an extra column, because a
spreadsheet lets them invent a second dimension when they need one.

The other half of the problem is when people are asked. A month later, looking at a list
of merchant names, nobody remembers what a particular Tuesday's charge was for, so they
guess, and the guesses pile up until the totals mean nothing. The moment someone knows is
the moment the card is charged. People who make many small payments a week won't file any
of them by hand, so whatever they see at the end of the week has to have sorted itself
out. And asking goes wrong when it never stops: a prompt is useful for purchases that need
a decision, but being asked about the same supermarket, bus fare, and streaming charge
every time, with the same answer for a year, teaches people to tap it away without
reading it.

### ASSUMPTIONS

- **Unverified.** That a charge can be surfaced to the user close enough to the moment it
  occurs for them to still remember its purpose. Settled by the same investigation that
  bounds 01-S01, plus a measurement of how long alerts from a given institution take to
  arrive.
- **Unverified.** That the platform permits an application to react to an incoming
  transaction notification in the background. Mobile platforms differ materially here, and
  at least one restricts reading notifications delivered to other applications. Settled by
  a spike on each target platform before any story here depends on it.
- **Assumed.** Merchant descriptors on transactions are inconsistent in spelling and
  padding within one institution but stable enough that a normalised form matches reliably.
- **Assumed.** Most people's spending concentrates on a small number of repeat merchants,
  so automatic categorization reaches useful accuracy from a modest number of corrections
  rather than requiring a trained model.
- **Assumed.** Category and spending group are genuinely independent: any category may
  appear under any group, and neither constrains the other.
- **Assumed.** Being asked about a transaction has a cost that rises with how often the
  answer was predictable. A prompt that fires for settled categories trains people to
  dismiss it, which destroys its value for the transactions that genuinely need a decision.
- **Assumed.** A transaction belongs to at most one group. Splitting a single charge
  across two groups is deliberately out of scope until someone asks for it.

### STORIES

* **02-S01** — **When** I file my spending against budgets and a charge's purpose fades
  from memory within days, **I want to** be asked which group a charge belongs to at the
  time it is charged, **so that** I can answer while I still remember what I bought.
  * The prompt offers the groups the person uses most, and answering takes one tap
  * Dismissing the prompt leaves the transaction unfiled rather than guessing, and it can
    be filed later
  * The prompt can be turned off entirely without affecting anything else in the product

* **02-S02** — **When** one charge answers two questions at once, what it was and which
  budget it belongs to, **I want to** give a transaction both a category and a spending
  group, **so that** I can ask what I spent on food and what my university budget cost me
  without the two answers competing.
  * Category and group are recorded independently, and either may be set without the other
  * Both are visible on the transaction and either can be changed afterwards
  * Totals can be produced by category, by group, or by both together

* **02-S03** — **When** I make many small payments a week and won't file any of them by
  hand, **I want to** have my transactions sorted into categories without doing it myself,
  **so that** I can see where my week went without filing anything.
  * A newly captured transaction receives a category automatically where one can be
    determined with confidence
  * Transactions the product cannot categorize confidently are marked as uncategorized
    rather than assigned a wrong category
  * Automatic categorization never overwrites a category a person set by hand

* **02-S04** — **When** the same merchant appears every month and I always file it the
  same way, **I want to** create a rule that files matching transactions automatically,
  **so that** I can stop answering the same question about the same merchant every month.
  * A rule matches on merchant, amount range, account, or a combination
  * A rule can set category, group, or both
  * Rules are listed in the order they apply and can be reordered, edited, and switched off

* **02-S05** — **When** the product has filed a transaction wrongly, **I want to** correct
  a categorization and have that correction remembered, **so that** I can fix a mistake
  once rather than every month.
  * Correcting a transaction offers to create or update a rule covering similar ones
  * The person chooses whether the correction applies only to this transaction, to future
    ones, or also to past ones
  * Applying a correction to past transactions reports how many were changed

* **02-S06** — **When** some of my transactions have been left without a category,
  **I want to** find the transactions that have not been categorized, **so that** I can
  clear them in one sitting instead of hunting for them.
  * Uncategorized transactions are reachable in one step from the main view
  * They can be categorized from that list without opening each one
  * The list shows how many remain

* **02-S07** — **When** most prompts ask about charges I have answered the same way many
  times, **I want to** have transactions whose category is already settled filed without
  being asked, **so that** I can be prompted only for the ones I actually need to decide.
  * A transaction matched by a rule from 02-S04 is filed silently and raises no prompt
  * Setting a default from a prompt is offered at the moment the person answers it, so
    settling a category costs nothing extra
  * The person can see which transactions were filed silently, and undo a default that
    turns out to be wrong

### NON-FUNCTIONAL REQUIREMENTS

- **Prompt latency.** Where a charge can be surfaced at all, the prompt appears within 60
  seconds of the product receiving it, since its entire value depends on arriving while
  the purchase is remembered.
- **Prompt cost.** Filing a transaction from the prompt takes exactly one interaction and
  requires no typing.
- **Prompt suppression.** A transaction matched by a rule raises no prompt. Prompt volume
  falls as defaults accumulate, and a person who has settled their recurring merchants
  sees prompts only for genuinely new ones.
- **Categorization accuracy.** After 30 user corrections in an account, at least 80% of
  newly captured transactions from previously seen merchants receive the category the user
  would have chosen. Accuracy is measured against subsequent corrections, not asserted.
- **Bulk correction performance.** Applying a rule retroactively across 5,000
  transactions completes within 5 seconds and reports the count changed.
- **Determinism.** Given the same transaction and the same rule set, categorization
  produces the same result every time, and the rule responsible is inspectable.
- **No silent overwriting.** No automatic process changes a category or group a person set
  by hand, under any circumstance.
- **Privacy of prompting.** A notification prompt discloses no amount or merchant on a
  locked screen unless the user has explicitly enabled that.
