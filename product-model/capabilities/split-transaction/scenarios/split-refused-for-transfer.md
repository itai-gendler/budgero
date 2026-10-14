---
kind: validation
routes:
  web: Web
steps:
- text: The User tries to split a transfer leg
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::account
- text: The transaction is a transfer
  kind: condition
  entities:
  - {entity: transaction, effect: reads, facts: [Transfer link]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product refuses because transfers cannot be split
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::account
---

# Refuse splitting a transfer

## Trigger

A person tries to split one leg of a transfer.

## Outcome

The transfer stays as it is.
