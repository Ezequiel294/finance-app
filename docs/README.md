# {{PRODUCT_NAME}} — Product Documentation

This directory holds the documents that define what {{PRODUCT_NAME}} is for and who it
serves. The rules governing how these documents are written, read, and updated live in
`openspec/specs/documentation/`. Read the relevant capability there before authoring or
revising anything here.

The product name has not been chosen. Until it is, every document refers to the product
as `{{PRODUCT_NAME}}`, so a single substitution pass will name it everywhere at once.

## Index

| Document | Covers |
|---|---|
| [`vision.md`](vision.md) | What the product is, who it is for, why they would choose it, and the principles and non-goals every story is checked against |
| [`backlog.md`](backlog.md) | The stories to take up next, in order, with the reason for each position |
| [`epics/`](epics/) | One file per epic: the situations it addresses, the assumptions behind it, its stories, and its non-functional requirements |

### Epics

| Document | Epic |
|---|---|
| [`01-accounts-and-transaction-ingestion.md`](epics/01-accounts-and-transaction-ingestion.md) | Accounts and Transaction Ingestion |
| [`02-categorization-and-rules.md`](epics/02-categorization-and-rules.md) | Categorization and Rules |
| [`03-budgets-and-limits.md`](epics/03-budgets-and-limits.md) | Budgets and Limits |
| [`04-dashboard-and-insights.md`](epics/04-dashboard-and-insights.md) | Dashboard and Insights |
| [`05-multi-currency-and-fx.md`](epics/05-multi-currency-and-fx.md) | Multi-Currency and Account Roles |
| [`06-security-and-data-control.md`](epics/06-security-and-data-control.md) | Security and Data Control |
| [`07-investments-and-net-worth.md`](epics/07-investments-and-net-worth.md) | Investments and Net Worth |

## How Work Flows

The rules for turning a story into working software live in `openspec/specs/process/`.
Read the relevant capability there before proposing, building, or merging anything.
Where a new idea goes (an existing story, a new story in an existing epic, or a new epic)
is decided by `documentation/epics`.

| Capability | Covers |
|---|---|
| `process/vertical-slices` | One change per story, built as ordered vertical slices that are each tested, working, and reviewed before the next begins |
| `process/backlog-flow` | The short backlog of what comes next, one active story per person, the Definition of Ready and Done, and spikes |
| `process/branching-and-releases` | Branches from `develop`, pull requests, merge commits, version tags, and releasing to `main` |
| `process/capability-layout` | Where product specs live, what a capability is, and what belongs in `architecture.md` instead |

## Implementation Status

Status is never written down. It is read from the specs when needed:

- **implemented**: a requirement in a product spec under `openspec/specs/` cites the story;
- **in progress**: only a requirement in an active change cites it;
- **not started**: nothing cites it.

Product specs are every spec outside `documentation/` and `process/`. To list the stories
in each state:

```sh
# implemented
grep -rhoE 'Realizes: .*' openspec/specs | grep -oE '[0-9]{2}-S[0-9]{2}' | sort -u
# in progress
grep -rhoE 'Realizes: .*' openspec/changes --exclude-dir=archive | grep -oE '[0-9]{2}-S[0-9]{2}' | sort -u
```

Every other story is not started. `openspec list` shows the changes in progress.
