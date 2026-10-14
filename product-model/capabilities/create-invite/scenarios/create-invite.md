---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Create Invite in a workspace they own
  kind: actor
  actor: user
  entities:
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::workspaces
- text: The Product creates a pending Invitation that expires in seven days and attaches the workspace key wrapped under its secret
  kind: product
  actor: user
  entities:
  - {entity: invitation, effect: creates, to: Pending, facts: [Invitee email, Expires at, Invite link]}
  - {entity: workspace, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::workspaces
- text: The Product shows the invite link to copy or email
  kind: condition
  entities:
  - {entity: invitation, effect: reads, facts: [Invite link]}
  contexts:
    web:
      place: web-app::signed-in::workspaces
---

# Create an invite link

## Trigger

A person wants their partner to share the budget.

## Outcome

A link is ready to send over a trusted channel; anyone holding it can redeem it once.
