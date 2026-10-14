---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Resume on a paused template
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
- text: The Product reactivates the Recurring transaction and generates its upcoming Occurrences
  kind: product
  actor: user
  entities:
  - {entity: recurring-transaction, effect: changes, from: Paused, to: Active, facts: []}
  - {entity: occurrence, effect: creates, to: Scheduled, facts: [Due date]}
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
---

# Resume a recurring transaction

## Trigger

The paused bill starts again.

## Outcome

Reminders and upcoming due dates are back.
