# Security and Data Control

### PROBLEM

Some people have already decided never to give an application the username and password
to their bank so it can fetch their transactions. They don't misunderstand the
technology. They understand it well enough to know that standing access to their account
is exactly what they would hand over. They don't want to be reassured, and a product that
tries to talk them out of it loses them at that screen. They are willing to download
their own statements and hand over a file, which gives the product everything it needs
and gives away nothing they aren't prepared to give.

The failure to guard against is a product that treats linking an account as the real path
and everything else as second best: the unlinked experience is a stub, the interface
nags, and half the views say they need a connection. For someone who won't link, that
isn't a lesser product; it is one they can't use. The same need comes from another
direction for people who carry their finances on a phone that goes everywhere with them:
a phone that can be picked up and opened reveals every account they hold, what they earn,
and where they shop. Both want the same thing: to decide what the product may see, and to
change their mind later without argument, negotiation, or a support request.

### ASSUMPTIONS

- **Assumed.** Every capability in the product except those explicitly requiring a
  connection works fully from imported and manually entered data. This is a design
  constraint on all other initiatives, not a feature of this one.
- **Assumed.** Where a connection exists at all, it issues a revocable token. The product
  never holds an institution password, and no story anywhere depends on it doing so.
- **Unverified.** Which jurisdictions' personal data obligations apply to the product's
  users. Costa Rica has a personal data protection statute with a supervisory authority,
  and further obligations may follow from where data is stored. Settled by identifying the
  applicable statutes and hosting locations, and recording them here with citations.
- **Assumed.** Device-level biometric or passcode authentication is available on the
  platforms targeted and is the appropriate lock, rather than the product inventing its own.
- **Assumed.** Export must be in a format usable elsewhere without the product, since an
  export that only this product can read is not a way out.
- **Assumed.** Deletion means deletion. Retaining data after a deletion request for
  analytics or recovery is out of scope and is not done.

### STORIES

* **06-S01** — **When** I have decided never to give an application my banking
  credentials, **I want to** use every part of the product without linking any account,
  **so that** I can keep my banking credentials to myself and still get the whole benefit.
  * No view, total, or budget is unavailable or degraded solely because no account is
    connected
  * The product does not prompt the person to connect an account after they have declined
    once
  * Any capability that genuinely requires a connection states so plainly at the point of
    use, rather than appearing broken

* **06-S02** — **When** I have given the product access to some of my information, **I want
  to** see exactly what the product can currently access and withdraw any of it
  immediately, **so that** I can decide what it may see and change my mind whenever I
  want.
  * One screen lists every connection, import source, and shared budget, and what each
    exposes
  * Revoking takes effect immediately, without a support request or a waiting period
  * Revoking states plainly what will stop working and what data is removed

* **06-S03** — **When** my finances are on a phone that others can pick up, **I want to**
  require my device's own lock before the product opens, **so that** I can hand someone my
  phone without handing them my finances.
  * Uses the device's existing biometric or passcode mechanism rather than a separate
    password
  * Locks again after a period of inactivity that the person sets
  * Locking is enforced on the web as well, by ending an idle session

* **06-S04** — **When** I might want to stop using the product one day, **I want to** take
  all my data out in a format I can open elsewhere, **so that** I can leave whenever I
  choose without losing what I have recorded.
  * Export covers transactions, categories, groups, budgets, and holdings
  * The format opens in a spreadsheet application with no conversion step
  * Export completes without needing to contact anyone

* **06-S05** — **When** I have decided to stop using the product, **I want to** delete my
  data and know it is gone, **so that** I can end my relationship with the product
  completely.
  * Deletion covers everything held about the person, including anything derived from
    their data
  * The person is told what will be deleted before confirming, and how long it takes
  * Completion is confirmed to the person rather than assumed

* **06-S06** — **When** I have lost the phone I use the product on, **I want to** get back
  into my account if I lose my phone, **so that** I can recover without losing everything
  I have recorded.
  * Recovery does not depend on the lost device
  * Recovery does not require exposing the person's data to anyone
  * A recovered session requires the lock in 06-S03 to be re-established before use

### NON-FUNCTIONAL REQUIREMENTS

- **Credential storage.** No institution password is ever stored, transmitted, or logged
  by the product, under any configuration.
- **Token custody.** Connection tokens are held server-side only, never written into the
  application bundle or device storage, and are revocable independently per connection.
- **Encryption at rest.** All personal financial data is encrypted at rest with AES-256 or
  equivalent. Device-local caches use the platform's own protected storage.
- **Encryption in transit.** TLS 1.3 or later for all traffic. Certificate validation
  failures terminate the connection rather than prompting the user to continue.
- **Authentication.** Device biometric or passcode for the application; idle sessions end
  after a user-set period defaulting to 15 minutes.
- **Revocation latency.** A revocation takes effect within 5 seconds and is irreversible
  without the user re-granting access.
- **Deletion service level.** A deletion request completes within 30 days, including
  backups, and the user is notified on completion. No derived or aggregated copy of the
  deleted data is retained.
- **Data minimisation.** Only data required by a capability the user has enabled is
  collected. Transaction data is never transmitted to any third party for advertising,
  analytics, or resale, under any circumstance.
- **Logging.** Application logs never contain account numbers, balances, transaction
  amounts, or merchant names.
- **Breach notification.** Affected users are notified within 72 hours of confirming a
  breach involving personal financial data.
