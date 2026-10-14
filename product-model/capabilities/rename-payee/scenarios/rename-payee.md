---
kind: primary
routes:
  web: Web
steps:
- text: The User renames a payee
  kind: actor
  actor: user
  entities:
  - {entity: payee, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::payees
- text: The Product renames the Payee and updates every Transaction carrying the old name, merging into an existing payee of the new name
  kind: product
  actor: user
  entities:
  - {entity: payee, effect: changes, facts: [Name]}
  - {entity: transaction, effect: changes, facts: [Payee]}
  contexts:
    web:
      place: web-app::signed-in::payees
---

# Rename a payee

## Trigger

Two spellings of one shop should become one.

## Outcome

Every transaction shows the new name.
