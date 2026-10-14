---
kind: validation
routes:
  web: Web
steps:
- text: The User deletes an account
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The account holds transactions or a non-zero balance
  kind: condition
  entities:
  - {entity: transaction, effect: reads, facts: [Date]}
  - {entity: account, effect: reads, facts: [Balance]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product refuses and asks to move or delete its transactions first
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Refuse deleting an account that has transactions

## Trigger

A person tries to delete an account with history.

## Outcome

The account stays; archiving is the way to close it.
