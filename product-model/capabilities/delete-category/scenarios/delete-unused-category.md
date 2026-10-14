---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes a category that never had transactions or money assigned, and confirms
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  - {entity: transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product deletes the Category together with its Goal
  kind: product
  actor: user
  entities:
  - {entity: category, effect: removes}
  - {entity: goal, effect: removes, with: category}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Delete a category that was never used

## Trigger

A person removes a category they never used.

## Outcome

The category and its goal are gone; nothing else in the budget changes.
