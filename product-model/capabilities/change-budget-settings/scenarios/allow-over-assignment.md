---
kind: primary
routes:
  web: Web
steps:
- text: The User allows assigning beyond Ready to Assign
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::budget-settings
- text: The Product saves the setting for the Workspace
  kind: product
  actor: user
  entities:
  - {entity: workspace, effect: changes, facts: [Allow over-assignment]}
  contexts:
    web:
      place: web-app::signed-in::budget-settings
---

# Allow over-assignment

## Trigger

A person wants to assign money they expect but have not recorded yet.

## Outcome

Assignments and goal funding may take Ready to Assign below zero in every budget of the workspace.

## Edge cases

- Turning it off again refuses further assignments beyond Ready to Assign; existing negative Ready to Assign stays.
