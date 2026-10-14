---
kind: validation
routes:
  web: Web
steps:
- text: The User deletes a group
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The group still contains categories
  kind: condition
  entities:
  - {entity: category, effect: reads, facts: [Group]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product refuses and asks to move or delete them first
  kind: product
  actor: user
  entities:
  - {entity: category-group, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Refuse deleting a group that still holds categories

## Trigger

A person tries to delete a group that is not empty.

## Outcome

The group and its categories stay.

## Edge cases

- The Income group can never be deleted.
