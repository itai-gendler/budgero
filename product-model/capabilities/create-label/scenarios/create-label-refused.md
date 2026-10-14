---
kind: validation
routes:
  web: Web
steps:
- text: The User saves a label
  kind: actor
  actor: user
  entities:
  - {entity: label, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::labels
- text: The name is empty or already used, or the colour is not a valid colour
  kind: condition
  entities:
  - {entity: label, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::labels
- text: The Product refuses the Label
  kind: product
  actor: user
  entities:
  - {entity: label, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::labels
---

# Refuse an invalid label

## Trigger

A person repeats a label name.

## Outcome

No label is created.
