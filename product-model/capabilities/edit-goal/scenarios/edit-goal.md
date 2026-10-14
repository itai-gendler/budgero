---
kind: primary
routes:
  web: Web
steps:
- text: The User changes a goal's target and chooses Update Goal
  kind: actor
  actor: user
  entities:
  - {entity: goal, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product saves the Goal and recomputes what the category needs
  kind: product
  actor: user
  entities:
  - {entity: goal, effect: changes, facts: [Target type, Target amount, Target date, Repeats]}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The category's assignments are unchanged
  kind: condition
  entities:
  - {entity: assignment, effect: reads, facts: [Amount]}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Edit a goal

## Trigger

A target stopped fitting reality.

## Outcome

The goal asks for a new amount from now on; money already in the category stays.
