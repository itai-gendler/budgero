---
kind: validation
routes:
  web: Web
steps:
- text: The User chooses Create Invite
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::workspaces
- text: Members and pending invitations across the workspaces the User owns already occupy five seats
  kind: condition
  entities:
  - {entity: workspace-membership, effect: reads, facts: [Role]}
  - {entity: invitation, effect: reads, facts: [Expires at]}
  - {entity: user, effect: reads, facts: []}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::workspaces
- text: The Product refuses and asks to remove a member or cancel a pending invitation first
  kind: product
  actor: user
  entities:
  - {entity: invitation, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::workspaces
---

# Refuse an invite when every seat is taken

## Trigger

An owner has already shared with five people.

## Outcome

No invitation is created.
