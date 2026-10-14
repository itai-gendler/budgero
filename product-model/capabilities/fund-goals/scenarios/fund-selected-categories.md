---
kind: primary
routes:
  web: Web
steps:
- text: The User selects categories and chooses to fund goals from the budgeting side panel
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  - {entity: goal, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product funds the selected categories' goals with the same priority rules
  kind: product
  actor: user
  entities:
  - {entity: goal, effect: reads, facts: [Needed this month, Status]}
  - {entity: category, effect: reads, facts: [Funding priority]}
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  - {entity: rule, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product raises the selected categories' Assignments in one batch
  kind: product
  actor: user
  entities:
  - {entity: assignment, effect: changes, facts: [Amount]}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Fund only the selected categories

## Trigger

A person wants to fund a few goals now and leave the rest.

## Outcome

Only the selected categories receive money; categories outside the selection are untouched.
