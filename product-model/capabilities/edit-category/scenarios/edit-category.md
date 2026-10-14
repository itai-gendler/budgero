---
kind: primary
routes:
  web: Web
steps:
- text: The User edits a category's name, budget pace exclusion and funding priority and saves
  kind: actor
  actor: user
  entities:
  - {entity: budget, effect: reads, facts: []}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product saves the Category; its history, assignments and goal stay with it
  kind: product
  actor: user
  entities:
  - {entity: category, effect: changes, facts: [Name, Exclude from budget pace, Funding priority]}
  - {entity: assignment, effect: reads, facts: []}
  - {entity: goal, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Edit a category

## Trigger

A person renames a category or changes how it is treated.

## Outcome

The category shows the new details; reports and history follow it.
