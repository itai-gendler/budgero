---
kind: validation
routes:
  web: Web
steps:
- text: The User chooses Mark ready
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
- text: The template is not a transfer and has no category
  kind: condition
  entities:
  - {entity: recurring-transaction, effect: reads, facts: [Category]}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
- text: The Product refuses and asks for a category first
  kind: product
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
---

# Refuse posting an occurrence without a category

## Trigger

A template was saved without a category.

## Outcome

Nothing is posted and the occurrence stays scheduled.
