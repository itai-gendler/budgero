---
kind: edge
routes:
  web: Web
steps:
- text: The User raises a category's Assigned amount by more than Ready to Assign
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: Allow over-assignment is on for the workspace
  kind: condition
  entities:
  - {entity: workspace, effect: reads, facts: [Allow over-assignment]}
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  - {entity: assignment, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product warns that Ready to Assign will go negative and records the Assignment
  kind: product
  actor: user
  entities:
  - {entity: assignment, effect: changes, facts: [Amount]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: Ready to Assign is negative
  kind: condition
  entities:
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Assign beyond Ready to Assign when over-assignment is allowed

## Trigger

A person with over-assignment allowed funds a category beyond the money available.

## Outcome

The assignment is saved and Ready to Assign shows the negative shortfall prominently.
