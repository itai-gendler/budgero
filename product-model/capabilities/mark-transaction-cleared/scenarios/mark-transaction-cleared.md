---
kind: primary
routes:
  web: Web
steps:
- text: The User marks an uncleared transaction cleared
  kind: actor
  actor: user
  entities:
  - {entity: transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product marks the Transaction cleared
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: changes, from: Uncleared, to: Cleared, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Account's cleared balance includes it
  kind: condition
  entities:
  - {entity: account, effect: reads, facts: [Cleared balance]}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Mark a transaction cleared

## Trigger

A transaction shows up on the bank statement.

## Outcome

The cleared balance moves toward what the bank shows.

## Edge cases

- Marking several selected transactions at once skips reconciled ones.
