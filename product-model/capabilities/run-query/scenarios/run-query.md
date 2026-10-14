---
kind: primary
routes:
  web: Web
steps:
- text: The User writes a query, or picks a common one, and runs it
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::explorer
- text: The Product shows the result rows from the budget's Transactions and other data
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: reads, facts: [Date, Inflow, Outflow, Payee, Category]}
  - {entity: budget, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::explorer
---

# Run a query

## Trigger

A person asks a question no prebuilt report answers.

## Outcome

The rows can be charted or downloaded as CSV.
