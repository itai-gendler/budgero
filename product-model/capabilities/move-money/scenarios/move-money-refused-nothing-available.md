---
kind: validation
routes:
  web: Web
steps:
- text: The User asks to move money from a category
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The amount is not positive or the category has nothing available
  kind: condition
  entities:
  - {entity: category, effect: reads, facts: [Available]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product refuses and asks for a positive amount within available funds
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Refuse moving money a category does not have

## Trigger

A person tries to move money out of an empty or overspent category.

## Outcome

No assignment changes.
