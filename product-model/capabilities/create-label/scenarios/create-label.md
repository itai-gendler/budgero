---
kind: primary
routes:
  web: Web
steps:
- text: The User adds a label with a name and colour
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
  - {entity: label, effect: creates, facts: [Name, Color]}
  contexts:
    web:
      place: web-app::signed-in::labels
---

# Create a label

## Trigger

A person wants to track a holiday across categories.

## Outcome

The label can be put on transactions.
