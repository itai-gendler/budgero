---
kind: validation
routes:
  web: Web
steps:
- text: The User adds an income category with a name another income category already has
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget-settings
- text: The name matches an existing income category, ignoring case
  kind: condition
  entities:
  - {entity: category, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::budget-settings
- text: The Product refuses the new income category
  kind: product
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget-settings
---

# Refuse a duplicate income category name

## Trigger

A person repeats an income category name.

## Outcome

No category is created.

## Edge cases

- An empty income category name is refused too.
