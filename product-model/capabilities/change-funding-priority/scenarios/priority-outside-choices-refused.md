---
kind: validation
routes:
  web: Web
steps:
- text: The User applies a funding priority
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The priority is not a positive whole number, or is above 5 while the budget uses five levels
  kind: condition
  entities:
  - {entity: budget, effect: reads, facts: [Priority choices]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product refuses the change
  kind: product
  actor: user
  entities:
  - {entity: category, effect: reads, facts: [Funding priority]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Refuse a priority outside the budget's choices

## Trigger

A person enters a priority the budget does not allow.

## Outcome

No category priority changes.
