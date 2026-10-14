---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Manage budget and changes its name, icon or number format
  kind: actor
  actor: user
  entities:
  - {entity: budget, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product saves the Budget
  kind: product
  actor: user
  entities:
  - {entity: budget, effect: changes, facts: [Name, Icon, Number format]}
  contexts:
    web:
      place: web-app::signed-in
---

# Edit a budget's details

## Trigger

A person renames or restyles a budget.

## Outcome

The budget list shows the new details.
