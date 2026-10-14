---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete Goal on a category
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  - {entity: goal, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product removes the Goal; the category's assignments stay
  kind: product
  actor: user
  entities:
  - {entity: goal, effect: removes}
  - {entity: assignment, effect: reads, facts: [Amount]}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Delete a goal

## Trigger

A person no longer wants a target for a category.

## Outcome

The category is a plain envelope again with its money intact.
