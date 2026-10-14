---
kind: validation
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
- text: Allow over-assignment is off for the workspace
  kind: condition
  entities:
  - {entity: workspace, effect: reads, facts: [Allow over-assignment]}
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  - {entity: assignment, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product refuses the change and states by how much it would exceed Ready to Assign
  kind: product
  actor: user
  entities:
  - {entity: category, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Refuse an assignment beyond Ready to Assign

## Trigger

A person tries to assign more money than has no job yet.

## Outcome

The Assignment is unchanged and Ready to Assign stays where it was.
