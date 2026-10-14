---
kind: primary
routes:
  web: Web
steps:
- text: The User changes a template's amount, category or memo
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
- text: The Product saves the Recurring transaction; forecasts recalculate from it
  kind: product
  actor: user
  entities:
  - {entity: recurring-transaction, effect: changes, facts: [Amount, Category, Memo]}
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
---

# Edit a recurring amount

## Trigger

A subscription price changes.

## Outcome

Future occurrences post the new amount; posted transactions are unchanged.
