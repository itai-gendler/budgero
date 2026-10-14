---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Pause on a template
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
- text: The Product pauses the Recurring transaction
  kind: product
  actor: user
  entities:
  - {entity: recurring-transaction, effect: changes, from: Active, to: Paused, facts: []}
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
---

# Pause a recurring transaction

## Trigger

A gym membership is on hold.

## Outcome

No reminders arrive and its occurrences cannot be posted until it is resumed.
