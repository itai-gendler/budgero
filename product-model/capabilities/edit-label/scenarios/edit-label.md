---
kind: primary
routes:
  web: Web
steps:
- text: The User changes a label's name or colour
  kind: actor
  actor: user
  entities:
  - {entity: label, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::labels
- text: The Product saves the Label
  kind: product
  actor: user
  entities:
  - {entity: label, effect: changes, facts: [Name, Color]}
  contexts:
    web:
      place: web-app::signed-in::labels
---

# Edit a label

## Trigger

A label needs a clearer name.

## Outcome

Labelled transactions show the new label.
