---
kind: primary
routes:
  web: Web
steps:
- text: The User opens an invite link, or pastes an invite code, and enters their master password
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::join-workspace
- text: The Product decrypts the shared workspace key with the link's secret and re-wraps it under the User's master password on the device
  kind: product
  actor: user
  entities:
  - {entity: invitation, effect: reads, facts: [Invite link]}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::join-workspace
- text: The Product adds the User as a member and marks the Invitation redeemed
  kind: product
  actor: user
  entities:
  - {entity: workspace-membership, effect: creates, facts: [Role, Joined at]}
  - {entity: invitation, effect: changes, from: Pending, to: Redeemed, facts: []}
  contexts:
    web:
      place: web-app::signed-in::join-workspace
- text: The Product opens the shared Workspace
  kind: condition
  entities:
  - {entity: workspace, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::join-workspace
---

# Join a workspace with an invite link

## Trigger

A person received an invite link from a workspace owner.

## Outcome

They see and edit the same budgets as everyone else in the workspace, unlocked with their own master password.
