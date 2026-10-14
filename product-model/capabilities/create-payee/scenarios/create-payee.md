---
kind: primary
routes:
  web: Web
steps:
- text: The User adds a payee name
  kind: actor
  actor: user
  entities:
  - {entity: payee, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::payees
- text: The Product saves the Payee
  kind: product
  actor: user
  entities:
  - {entity: payee, effect: creates, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::payees
---

# Create a payee

## Trigger

A person wants a payee offered before using it.

## Outcome

The payee is offered when entering transactions.

## Edge cases

- Payees typed on transactions join the directory on their own.
