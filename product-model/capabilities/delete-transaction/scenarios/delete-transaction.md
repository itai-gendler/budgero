---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes a transaction
  kind: actor
  actor: user
  entities:
  - {entity: transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product removes the Transaction and corrects the Account's balances
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: removes, from: Uncleared}
  - {entity: account, effect: reads, facts: [Balance]}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Delete a transaction

## Trigger

A person removes a duplicate entry.

## Outcome

The entry is gone and balances and categories no longer count it.
