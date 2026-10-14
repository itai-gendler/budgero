---
kind: primary
routes:
  web: Web
steps:
- text: The User adds a group with a name to the budget table
  kind: actor
  actor: user
  entities:
  - {entity: budget, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product creates the Category group
  kind: product
  actor: user
  entities:
  - {entity: category-group, effect: creates, facts: [Name, Position, System group]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Create a category group

## Trigger

A person wants a new shelf for related categories.

## Outcome

The empty group appears in the budget table.
