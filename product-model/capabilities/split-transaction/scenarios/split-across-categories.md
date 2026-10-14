---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Split on a transaction and enters lines with categories and amounts
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  - {entity: transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product checks that the lines add up exactly to the total
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: reads, facts: [Inflow, Outflow]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product saves the Transaction's split lines, replacing any earlier ones
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: changes, facts: [Split lines]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: Each line's category shows its part as activity
  kind: condition
  entities:
  - {entity: category, effect: reads, facts: [Activity]}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Split a transaction across categories

## Trigger

One receipt covers groceries and household items.

## Outcome

The transaction stays one register entry while each category gets its share.
