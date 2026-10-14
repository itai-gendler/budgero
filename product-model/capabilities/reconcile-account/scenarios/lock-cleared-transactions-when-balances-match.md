---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Reconcile and enters the balance the bank shows
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::account
- text: It equals the Account's cleared balance
  kind: condition
  entities:
  - {entity: account, effect: reads, facts: [Cleared balance]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product locks every cleared Transaction dated today or earlier as reconciled and stamps the Account
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: changes, from: Cleared, to: Reconciled, facts: []}
  - {entity: account, effect: changes, facts: [Reconciled at]}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Reconcile an account whose balance matches

## Trigger

A person checks the account against a statement.

## Outcome

The cleared transactions are verified history and the account shows when it was reconciled; uncleared ones stay open.
