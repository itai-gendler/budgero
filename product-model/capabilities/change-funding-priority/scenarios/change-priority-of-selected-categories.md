---
kind: primary
routes:
  web: Web
steps:
- text: The User selects categories and applies a funding priority
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product sets the Funding priority of every selected Category together, undoable in one step
  kind: product
  actor: user
  entities:
  - {entity: category, effect: changes, facts: [Funding priority]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Change the priority of selected categories

## Trigger

A person decides which goals Fund Goals should serve first.

## Outcome

The selected categories share the new priority; badges show it when priority badges are on.

## Edge cases

- A selection with different priorities shows them as Mixed until one is applied.
