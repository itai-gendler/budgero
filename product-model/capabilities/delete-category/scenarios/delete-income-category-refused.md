---
kind: validation
routes:
  web: Web
steps:
- text: The User tries to delete the system Income category
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product refuses because the Income category cannot be edited or deleted
  kind: product
  actor: user
  entities:
  - {entity: category, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Refuse deleting the Income category

## Trigger

A person tries to delete the category that feeds Ready to Assign.

## Outcome

The Income category stays.
