---
kind: primary
routes:
  web: Web
steps:
- text: The User cancels a pending invitation of a workspace they own
  kind: actor
  actor: user
  entities:
  - {entity: workspace, effect: reads, facts: []}
  - {entity: invitation, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::workspaces
- text: The Product deletes the Invitation, freeing its seat
  kind: product
  actor: user
  entities:
  - {entity: invitation, effect: removes, from: Pending}
  contexts:
    web:
      place: web-app::signed-in::workspaces
---

# Cancel a pending invitation

## Trigger

An invite link was sent to the wrong person.

## Outcome

The link no longer works.
