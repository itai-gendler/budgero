---
kind: primary
routes:
  web: Web
steps:
- text: The User edits a group's name
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product saves the Category group's new name
  kind: product
  actor: user
  entities:
  - {entity: category-group, effect: changes, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Rename a category group

## Trigger

A person renames a shelf of the budget.

## Outcome

The group shows the new name; nothing else changes.

## Edge cases

- An empty name is refused.
- The Income group cannot be renamed.
