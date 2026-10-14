---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes a workspace they own and confirms
  kind: actor
  actor: user
  entities:
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::workspaces
- text: The Product deletes the Workspace with its budgets, memberships and pending invitations
  kind: product
  actor: user
  entities:
  - {entity: workspace, effect: removes}
  - {entity: budget, effect: removes, with: workspace}
  - {entity: workspace-membership, effect: removes, with: workspace}
  - {entity: invitation, effect: removes, from: Pending, with: workspace}
  contexts:
    web:
      place: web-app::signed-in::workspaces
---

# Delete a workspace

## Trigger

A household stops sharing a budget space.

## Outcome

The workspace and all its data are gone permanently for every member.
