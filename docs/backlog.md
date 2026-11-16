# Product Backlog

This lists only the stories chosen to come next, in the order they will be taken up. A
story not listed here has no order yet; find it in its epic under [`epics/`](epics/).

- When a story is added here, its detail bullets are written in its epic in the same edit.
- A story leaves this list in the same change that archives it.
- Status is never written here. It comes from the specs (see [`README.md`](README.md)).

The next story to take up is the first one listed whose Definition of Ready is met. The
rules for this document, and the Definition of Ready and Done, are in
`openspec/specs/process/backlog-flow/`.

## Next

The first path runs from capturing a charge, through organizing it, to reviewing where the
money went, so the product does something useful end to end as early as possible.

| # | Story | I want to | Why here |
|---|---|---|---|
| 1 | `01-S03` | add a transaction by hand in a few seconds | The walking skeleton. It is the smallest complete behavior in the product, so it can stand up every layer with nothing else to get wrong. |
| 2 | `01-S06` | see every account I hold and its current balance in one list | Turns captured transactions into the first figure worth opening the product for, and brings in accounts beyond the single one the skeleton needs. |
| 3 | `01-S05` | record a payment that has arrived from a client | Reuses the entry form and adds money coming in, which every later total depends on. |
| 4 | `02-S02` | give a transaction both a category and a spending group | Introduces the category and spending-group dimensions that every budget and chart is built on. |
| 5 | `02-S06` | find the transactions that have not been categorized | Makes categorizing by hand workable before any automation exists. |
| 6 | `04-S01` | see where last month's money went | The first answer the product gives back. With it, the path from capturing a charge to learning something from it runs end to end. |
