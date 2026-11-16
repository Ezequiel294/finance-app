# Product Vision

## Vision Statement

**FOR** people who manage their money across more than one bank and more than one
currency, and who have fallen back on a spreadsheet because no application understands
how they actually move money,
**WHO** need to know where their money goes and what they are worth without spending an
evening every month re-entering it by hand,
**THE** {{PRODUCT_NAME}} **is a** cross-platform personal finance dashboard
**THAT** captures each charge close to the moment it happens and asks one question to
file it, keeps colones and dollars distinct rather than silently blending them, ignores
money moved between a person's own accounts, and values held investments at live prices
net of the fees it would take to cash out,
**UNLIKE** consumer expense trackers built around a single bank and a single currency,
whose automatic capture misfires and whose foreign-currency support is an afterthought —
or a spreadsheet, which is accurate only for as long as someone keeps feeding it,
**OUR PRODUCT** treats multiple accounts, multiple currencies, and fee-aware asset
valuation as the normal case rather than the exception.

## What, Who, and Why

**What it is.** A personal finance dashboard that runs on phones and in a browser. It
brings transactions together from whatever sources a person's banks actually expose,
files them against both a spending category and the budget they belong to, and presents
spending, budgets, and net worth in one place. What distinguishes it from existing
trackers is that it assumes the messy case: several institutions, two currencies,
deliberate transfers between one's own accounts, and assets whose real value depends on
what it costs to sell them.

**Who it is for.** Individuals and households whose finances are split across
institutions by choice or by circumstance — people who keep savings at one bank and spend
from another, who earn in one currency and spend in another, or who separate money
deliberately as a safety measure. It is equally for people with a single account and a
single currency who simply want to know where their money went, and for people whose
income arrives irregularly and who need to know what is safe to spend.

**Why they would choose it.** Because the alternatives make them do the work. A
spreadsheet is completely flexible and completely manual, and it is accurate only in the
days right after someone updates it. Existing trackers automate some of the capture but
get the details wrong that matter most to this user: they count a transfer between two of
your own accounts as spending, they convert currencies behind your back or refuse to
handle them at all, and they show an investment's market value without acknowledging the
fees standing between that number and money in your pocket. {{PRODUCT_NAME}} is built
around those details rather than in spite of them.

## Principles

Every epic and story must follow these. Each one can be checked.

- **Fully usable without linking any account.** Everything the product does must also
  work for someone who never links a bank.
- **Useful with one account, one currency, and no setup.** Someone with a single account
  in a single currency must get value without configuring anything first.

## Non-goals

The product deliberately leaves these out.

- **Financial advice or recommendations.** {{PRODUCT_NAME}} describes what a person's
  money has done and what it is worth now. It does not recommend, rank, or project.
  Serving advisors would pull it toward giving advice.
- **Tax and accounting.** Tax rules depend on the country, change every year, and matter
  to few users. The product has no way to keep them correct. People who need this can
  export their transactions and work elsewhere.
- **Businesses and organisations.** Company finances bring several approvers, payroll,
  receivables, and audits. No individual needs these, and supporting them would reshape
  every feature.
- **Running anything on a bank's or institution's side.** The product uses whatever an
  institution exposes. It never administers anything for the institution, so no bank
  staff configure, operate, or support it.

## Using This Vision

Every epic and story for {{PRODUCT_NAME}} is checked against this vision, including its
principles and non-goals. If the vision doesn't support an idea, the idea is dropped, or
the vision is changed first on purpose. A vision change goes in its own commit, and the
commit message says what changed and why. The vision keeps the product from collecting
features that no longer serve the people it was built for.
