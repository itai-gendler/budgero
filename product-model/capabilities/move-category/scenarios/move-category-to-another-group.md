---
kind: primary
routes:
  web: Web
steps:
- text: The User drags a category into another category group
  kind: actor
  actor: user
  entities:
  - {entity: category-group, effect: reads, facts: [Name]}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product moves the Category to that group and saves the new order
  kind: product
  actor: user
  entities:
  - {entity: category, effect: changes, facts: [Group]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Move a category to another group

## Trigger

A person reorganises the budget table.

## Outcome

The category sits in its new group with all its history.
