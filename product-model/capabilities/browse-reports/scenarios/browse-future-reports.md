---
kind: edge
routes:
  web: Web
steps:
- text: The User picks a range reaching past today, such as Next 3 months
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::reports
- text: The Product counts scheduled Occurrences as if posted on their due dates and notes that projections are included
  kind: product
  actor: user
  entities:
  - {entity: occurrence, effect: reads, facts: [Due date]}
  - {entity: recurring-transaction, effect: reads, facts: [Amount, Category]}
  contexts:
    web:
      place: web-app::signed-in::reports
---

# Read reports for a future period

## Trigger

A person wants to see cash flow through the end of the quarter.

## Outcome

The report forecasts from recurring templates; posting or skipping an occurrence updates it.
