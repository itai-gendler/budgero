---
kind: validation
routes:
  web: Web
steps:
- text: The User tries to create a workspace on Budgero Cloud
  kind: actor
  actor: user
  entities:
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::workspaces
- text: The User has no active subscription, trial, founding membership or beta access
  kind: condition
  entities:
  - {entity: user, effect: reads, facts: [Workspace access]}
  - {entity: workspace-membership, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::workspaces
- text: The Product refuses and offers to redeem an invitation or subscribe
  kind: product
  actor: user
  entities:
  - {entity: invitation, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::workspaces
---

# Refuse a workspace without workspace access

## Trigger

A person without a plan tries to own a workspace.

## Outcome

No workspace is created; joining someone else's workspace is still possible.
