# Dashboard and Insights

### PROBLEM

Many people can list what they spent yesterday and have no idea what they spent last
month. The information exists in their banking app, one screen at a time, in the order it
happened, with no sense of which of forty lines mattered. Reading a list in date order
never tells them that a third of their money goes on eating out. They don't want to study
their finances. They want to glance at something and come away with one fact they didn't
have before. People who already track their totals by hand have a sharper version: they
know their totals, and what their spreadsheet can't easily show is whether this month is
unusual. A number by itself is not information. A number next to the three months before
it is.

Products usually fail here by answering with decoration: a colourful chart that is
pleasant to look at, answers no question anyone asked, and can't be questioned when it
shows something surprising. When a category looks too high, the only useful next step is
to see the transactions behind it, at once, without going somewhere else and rebuilding
the filter by hand. People who share household costs need one more thing: the household
total broken down by who spent it, because that is what the recurring argument is about,
and no chart of categories will settle it.

### ASSUMPTIONS

- **Assumed.** A view is worth building only if it answers a question someone stated. Each
  story below names the question its view answers, and a view whose question cannot be
  stated is not built.
- **Assumed.** Comparison across periods is only meaningful once roughly three periods of
  data exist; before that the product shows totals rather than trends, and says why.
- **Assumed.** Mixed-currency totals must be handled explicitly rather than summed. How
  that is done is specified in `05-multi-currency-and-fx.md`; this initiative depends on
  it rather than restating it.
- **Assumed.** The primary device for reading a dashboard is a phone, and every view here
  is designed to be legible at phone width before it is designed for a larger screen.
- **Assumed.** Uncategorized transactions distort any breakdown, so they are shown as
  their own visible share rather than omitted or silently folded into another category.
- **Unverified.** That a single summary view can serve both someone who wants one fact
  and someone who wants to compare and drill in. Settled by putting the same view in
  front of both kinds of user; if it cannot, the view splits rather than accumulating
  controls.

### STORIES

* **04-S01** — **When** my spending is only visible as a long list in date order, **I want
  to** see where last month's money went, **so that** I can learn something about my
  spending without having recorded any of it.
  * Answers the question: *which categories took the largest share of what I spent?*
  * Categories are ordered by share, with the uncategorized share shown alongside them
  * The view is readable without interaction — no control has to be operated to get the
    answer

* **04-S02** — **When** I already know my totals but can't tell whether they are normal,
  **I want to** compare a period against the ones before it, **so that** I can tell
  whether this month is unusual or normal for me.
  * Answers the question: *is this period higher or lower than my recent periods, and by
    how much?*
  * Shows at least three prior periods where the data exists, and says so when it does not
  * The comparison is stated as a difference, not left for the reader to compute

* **04-S03** — **When** I file spending against budgets as well as categories, **I want
  to** see spending broken down by group as well as by category, **so that** I can find
  out what my university living actually costs me.
  * Answers the question: *how much did each of my budgets consume this period?*
  * Group and category breakdowns are reachable from the same view without renavigating
  * A group's total can be read alongside its limit where one is set

* **04-S04** — **When** a figure on a chart looks wrong to me, **I want to** open a part of
  a chart and see the transactions behind it, **so that** I can find out what made a
  number look wrong.
  * Answers the question: *what exactly produced this figure?*
  * Selecting any segment, bar, or row lists the transactions composing it
  * The resulting list carries the same period and filters, with no re-selection required

* **04-S05** — **When** I share household costs with someone and we disagree about who
  paid for what, **I want to** see our household spending split by who spent it, **so
  that** I can settle what each of us contributed without reconstructing it from two sets
  of statements.
  * Answers the question: *of what we spent together, how much did each of us pay for?*
  * Covers only transactions attributed to the shared budget
  * Each person's share is shown as both an amount and a proportion

* **04-S06** — **When** my income arrives in irregular lumps, **I want to** see my income
  alongside my spending over time, **so that** I can see how lumpy months actually compare
  against what I spent in them.
  * Answers the question: *when did money arrive, and how did spending track it?*
  * Incoming and outgoing amounts are distinguishable at a glance
  * Periods with no income are visible as such rather than rendered as gaps

### NON-FUNCTIONAL REQUIREMENTS

- **Render latency.** Any view here renders within 1.5 seconds over 5,000 transactions on
  a current mid-range phone, including the aggregation behind it.
- **Drill-through latency.** The transaction list behind a selected element appears within
  500 ms.
- **Phone-width legibility.** Every view is legible and fully operable at 360 px width
  with no horizontal scrolling and no truncation of figures.
- **Accessibility.** No view conveys information by colour alone; every series is
  distinguishable by label, pattern, or position. Text meets a 4.5:1 contrast ratio.
- **Honest emptiness.** A view with insufficient data says what is missing and what would
  fill it, rather than rendering an empty or misleading chart.
- **No silent currency mixing.** A total spanning currencies never presents a single
  figure without stating the conversion basis and the rate date.
- **Derivation.** Every figure can be expanded to the transactions that produced it.
