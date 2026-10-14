---
kind: primary
routes:
  web: Web
steps:
- text: The User enters an inflow categorised to an income category
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product records the Transaction
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount]}
  - {entity: category, effect: reads, facts: [Group]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: Ready to Assign rises by the inflow
  kind: condition
  entities:
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Add income

## Trigger

A paycheck arrives.

## Outcome

The money is ready to be given a job.

## Edge cases

- An inflow categorised to a spending category raises that category's Available instead of Ready to Assign.
- In Cumulative mode income dated after today counts only from its date.
