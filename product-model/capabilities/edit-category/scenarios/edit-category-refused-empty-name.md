---
kind: validation
routes:
  web: Web
steps:
- text: The User clears a category's name and saves
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product refuses the change
  kind: product
  actor: user
  entities:
  - {entity: category, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Refuse an empty category name

## Trigger

A person saves a category without a name.

## Outcome

The category keeps its previous details.

## Edge cases

- The system Income category cannot be renamed.
