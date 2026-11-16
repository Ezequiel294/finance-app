# Product Backlog

This is the order in which stories are taken up. It records order only. Whether a story
is built is derived from the specs and shown in the status table in [`README.md`](README.md);
it is never written here. A story leaves this list in the same change that archives it.

The next story to take up is the first one listed whose Definition of Ready is met. The
rules for this document, and the Definition of Ready and Done, are in
`openspec/specs/process/backlog-flow/`.

Split stories (`01-S01`, `03-S05`) are not listed; the stories that replaced them are.

## Ordered

The first path runs from capturing a charge, through organizing it, to reviewing where the
money went, so the product does something useful end to end as early as possible.

| # | Story | Persona | Wants to | Why here |
|---|---|---|---|---|
| 1 | `01-S03` | Daniela | add a transaction by hand in a few seconds | The baseline anchor and the walking skeleton. It is the smallest complete behavior in the product, so it can stand up every layer with nothing else to get wrong. |
| 2 | `01-S06` | Ezequiel | see every account I hold and its current balance in one list | Turns captured transactions into the first figure worth opening the product for, and brings in accounts beyond the single one the skeleton needs. |
| 3 | `01-S05` | Andrés | record a payment that has arrived from a client | Reuses the entry form and adds money coming in, which every later total depends on. |
| 4 | `02-S02` | Ezequiel | give a transaction both a category and a spending group | Introduces the category and spending-group dimensions that every budget and chart is built on. |
| 5 | `02-S06` | Daniela | find the transactions that have not been categorized | Makes categorizing by hand workable before any automation exists. |
| 6 | `04-S01` | Daniela | see where last month's money went | The first answer the product gives back. With it, the path from capturing a charge to learning something from it runs end to end. |

## Not Yet Ordered

Listed in 1-pager order. Position in this section implies nothing about priority; a story
moves into the ordered section when it is decided where it belongs.

### [Accounts and Transaction Ingestion](one-pagers/01-accounts-and-transaction-ingestion.md)

| Story | Persona | Wants to |
|---|---|---|
| `01-S02` | Patricia | import a statement file I downloaded from my bank |
| `01-S04` | Ezequiel | be shown transactions that look like duplicates of each other |
| `01-S07` | Ezequiel | see which of my institutions can be connected and which cannot |
| `01-S08` | Ezequiel | authorise a connection to an institution that supports one |
| `01-S09` | Ezequiel | be told when a connection has stopped working |

### [Categorization and Rules](one-pagers/02-categorization-and-rules.md)

| Story | Persona | Wants to |
|---|---|---|
| `02-S01` | Ezequiel | be asked which group a charge belongs to at the time it is charged |
| `02-S03` | Daniela | have my transactions sorted into categories without doing it myself |
| `02-S04` | Ezequiel | create a rule that files matching transactions automatically |
| `02-S05` | Ezequiel | correct a categorization and have that correction remembered |
| `02-S07` | Keisy | have transactions whose category is already settled filed without being asked |

### [Budgets and Limits](one-pagers/03-budgets-and-limits.md)

| Story | Persona | Wants to |
|---|---|---|
| `03-S01` | Daniela | be warned that I am running down the money I had for the month |
| `03-S02` | Ezequiel | set a separate limit for each spending group |
| `03-S03` | Andrés | see how much I can safely spend this period |
| `03-S04` | Andrés | see how long my current money lasts at my current rate of spending |
| `03-S06` | Ezequiel | confirm which of my recurring costs are commitments |
| `03-S07` | Patricia | invite my partner to a budget |
| `03-S08` | Patricia | see who paid for each transaction in our shared budget |
| `03-S09` | Patricia | end sharing whenever I decide to |
| `03-S10` | Keisy | set a budget over a week, a month, or a year |
| `03-S11` | Keisy | see what proportion of each budget I have used, including when I have gone past it |
| `03-S12` | Keisy | see what I would have saved by the end of the year if I stay inside my budgets |

### [Dashboard and Insights](one-pagers/04-dashboard-and-insights.md)

| Story | Persona | Wants to |
|---|---|---|
| `04-S02` | Ezequiel | compare a period against the ones before it |
| `04-S03` | Ezequiel | see spending broken down by group as well as by category |
| `04-S04` | Daniela | open a part of a chart and see the transactions behind it |
| `04-S05` | Patricia | see our household spending split by who spent it |
| `04-S06` | Andrés | see my income alongside my spending over time |

### [Multi-Currency and Account Roles](one-pagers/05-multi-currency-and-fx.md)

| Story | Persona | Wants to |
|---|---|---|
| `05-S01` | Ezequiel | see every amount in the currency it actually occurred in |
| `05-S02` | Ezequiel | choose a currency for my totals and see which rate produced them |
| `05-S03` | Ezequiel | mark two movements as a transfer between my own accounts |
| `05-S04` | Ezequiel | give each of my accounts a role |
| `05-S05` | Ezequiel | see what a currency conversion actually cost me |
| `05-S06` | Patricia | import a statement in a currency and have it stay in that currency |

### [Security and Data Control](one-pagers/06-security-and-data-control.md)

| Story | Persona | Wants to |
|---|---|---|
| `06-S01` | Patricia | use every part of the product without linking any account |
| `06-S02` | Patricia | see exactly what the product can currently access and withdraw any of it immediately |
| `06-S03` | Ezequiel | require my device's own lock before the product opens |
| `06-S04` | Patricia | take all my data out in a format I can open elsewhere |
| `06-S05` | Patricia | delete my data and know it is gone |
| `06-S06` | Daniela | get back into my account if I lose my phone |

### [Investments and Net Worth](one-pagers/07-investments-and-net-worth.md)

| Story | Persona | Wants to |
|---|---|---|
| `07-S01` | Ezequiel | record what I hold by entering it myself |
| `07-S02` | Ezequiel | see my holdings valued at current market prices |
| `07-S03` | Ezequiel | describe the fees my broker charges |
| `07-S04` | Ezequiel | record a contribution with the fees it actually incurred |
| `07-S05` | Ezequiel | see what I would actually receive if I sold everything today |
| `07-S06` | Ezequiel | see my accounts and my holdings in one total |
