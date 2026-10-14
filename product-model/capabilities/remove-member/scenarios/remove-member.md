---
kind: primary
routes:
  web: Web
steps:
- text: The User removes a member from a workspace they own
  kind: actor
  actor: user
  entities:
  - {entity: workspace-membership, effect: reads, facts: [Role]}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::workspaces
- text: The Product deletes the member's Membership and closes their live sync connection
  kind: product
  actor: user
  entities:
  - {entity: workspace-membership, effect: removes}
  contexts:
    web:
      place: web-app::signed-in::workspaces
---

# Remove a member

## Trigger

A person should no longer see the shared budget.

## Outcome

The former member stops receiving changes; data already on their device stays readable to them.

## Edge cases

- The owner's own membership cannot be removed.
