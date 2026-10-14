---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes a template and confirms
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
- text: The Product deletes the Recurring transaction with its Occurrences
  kind: product
  actor: user
  entities:
  - {entity: recurring-transaction, effect: removes, from: Active}
  - {entity: occurrence, effect: removes, from: Scheduled, with: recurring-transaction}
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
- text: Transactions already posted from it stay in the register
  kind: condition
  entities:
  - {entity: transaction, effect: reads, facts: [Date]}
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
---

# Delete a recurring transaction

## Trigger

A subscription was cancelled.

## Outcome

No more reminders or projections; the posted history remains.
