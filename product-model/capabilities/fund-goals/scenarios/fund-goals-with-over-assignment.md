---
kind: edge
routes:
  web: Web
steps:
- text: Allow over-assignment is on for the workspace
  kind: condition
  entities:
  - {entity: workspace, effect: reads, facts: [Allow over-assignment]}
  - {entity: assignment, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The User chooses Fund Goals
  kind: actor
  actor: user
  entities:
  - {entity: goal, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product funds every eligible shortfall regardless of Ready to Assign
  kind: product
  actor: user
  entities:
  - {entity: goal, effect: reads, facts: [Needed this month, Status]}
  - {entity: category, effect: reads, facts: [Funding priority]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product raises the Assignments in one batch
  kind: product
  actor: user
  entities:
  - {entity: assignment, effect: changes, facts: [Amount]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: Ready to Assign may be negative
  kind: condition
  entities:
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Fund the full shortfall when over-assignment is allowed

## Trigger

A person who allows over-assignment funds goals with little or no money left.

## Outcome

Every goal is funded for the month even if Ready to Assign goes below zero.
