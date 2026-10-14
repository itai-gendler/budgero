---
kind: edge
routes:
  web: Web
steps:
- text: The User lowers a category's Assigned amount
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product finds later months whose Available for the category would drop below zero
  kind: product
  actor: user
  entities:
  - {entity: category, effect: reads, facts: [Available]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product shows a future overspending warning listing those months and their projected Available
  kind: product
  actor: user
  entities:
  - {entity: assignment, effect: reads, facts: [Month]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The User chooses to proceed anyway
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product records the lower Assignment
  kind: product
  actor: user
  entities:
  - {entity: assignment, effect: changes, facts: [Amount]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Lower an assignment that would overspend a future month

## Trigger

A person takes money back from a category that later months already rely on.

## Outcome

The lower amount is saved after the person confirmed it; the listed future months now show negative Available.

## Edge cases

- Cancelling the warning leaves the assignment unchanged.
