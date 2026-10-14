---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Create workspace and enters a name
  kind: actor
  actor: user
  entities:
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::workspaces
- text: The Product creates the Workspace with the User as its owner
  kind: product
  actor: user
  entities:
  - {entity: workspace, effect: creates, facts: [Name, Allow over-assignment]}
  - {entity: workspace-membership, effect: creates, facts: [Role, Joined at], with: workspace}
  contexts:
    web:
      place: web-app::signed-in::workspaces
- text: The Product switches to the new workspace
  kind: condition
  entities:
  - {entity: workspace, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::workspaces
---

# Create a workspace

## Trigger

A person wants a separate space, such as for a family budget.

## Outcome

The new workspace is active and empty, ready for its first budget.
