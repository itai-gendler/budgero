---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes a budget and confirms
  kind: actor
  actor: user
  entities:
  - {entity: budget, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product deletes the Budget with its category groups
  kind: product
  actor: user
  entities:
  - {entity: budget, effect: removes}
  - {entity: category-group, effect: removes, with: budget}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product opens the workspace's remaining budget or the budget setup
  kind: condition
  entities:
  - {entity: workspace, effect: reads, facts: [Name]}
  - {entity: budget, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
---

# Delete a budget

## Trigger

A person no longer needs a budget.

## Outcome

The budget and its data are gone from the workspace on every device.
