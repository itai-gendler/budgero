---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes a group that holds no category
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product deletes the Category group
  kind: product
  actor: user
  entities:
  - {entity: category-group, effect: removes}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Delete an empty category group

## Trigger

A person removes a shelf they emptied.

## Outcome

The group is gone from the budget table.
