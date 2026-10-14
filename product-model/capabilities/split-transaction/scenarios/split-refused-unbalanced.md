---
kind: validation
routes:
  web: Web
steps:
- text: The User saves split lines
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::account
- text: The lines do not add up to the total
  kind: condition
  entities:
  - {entity: transaction, effect: reads, facts: [Inflow, Outflow, Split lines]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product refuses and shows the amount remaining
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::account
---

# Refuse split lines that do not add up

## Trigger

A person leaves part of the total unassigned to a line.

## Outcome

The previous split, if any, stays.

## Edge cases

- A line with both a category and a transfer account, or with neither, is refused.
