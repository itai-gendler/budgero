---
kind: primary
routes:
  web: Web
steps:
- text: The User marks a cleared transaction uncleared
  kind: actor
  actor: user
  entities:
  - {entity: transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product marks the Transaction uncleared
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: changes, from: Cleared, to: Uncleared, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Account's cleared balance leaves it out
  kind: condition
  entities:
  - {entity: account, effect: reads, facts: [Cleared balance]}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Mark a transaction uncleared

## Trigger

A person cleared an entry too early.

## Outcome

The transaction waits for the bank again.
