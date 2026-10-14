---
kind: validation
routes:
  web: Web
steps:
- text: The User tries to restore a backup
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::data-management
- text: The User is not the workspace owner or has no workspace access
  kind: condition
  entities:
  - {entity: workspace-membership, effect: reads, facts: [Role]}
  - {entity: user, effect: reads, facts: [Workspace access]}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::data-management
- text: The Product keeps restore unavailable; export stays available
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::data-management
---

# Refuse a restore without owner access

## Trigger

A member tries to restore a shared workspace.

## Outcome

Nothing is replaced.
