---
kind: edge
routes:
  web: Web
steps:
- text: The User changes a template's schedule
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
- text: The Product saves the Recurring transaction
  kind: product
  actor: user
  entities:
  - {entity: recurring-transaction, effect: changes, facts: [Schedule]}
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
- text: The Product replaces the scheduled Occurrences with ones from the new rhythm, keeping posted and skipped ones
  kind: product
  actor: user
  entities:
  - {entity: occurrence, as: old-occurrence, effect: removes, from: Scheduled}
  - {entity: occurrence, as: new-occurrence, effect: creates, to: Scheduled, facts: [Due date]}
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
---

# Change a recurring schedule

## Trigger

Rent moves from the 1st to the 15th.

## Outcome

Upcoming due dates follow the new schedule; history is untouched.
