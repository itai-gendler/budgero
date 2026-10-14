---
kind: validation
routes:
  web: Web
steps:
- text: The User submits an invite code
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::join-workspace
- text: The invitation is past its expiry
  kind: condition
  entities:
  - {entity: invitation, effect: reads, facts: [Expires at]}
  contexts:
    web:
      place: web-app::signed-in::join-workspace
- text: The Product marks the Invitation expired and refuses
  kind: product
  actor: user
  entities:
  - {entity: invitation, effect: changes, from: Pending, to: Expired, facts: []}
  contexts:
    web:
      place: web-app::signed-in::join-workspace
---

# Refuse an expired invitation

## Trigger

A person opens an invite link more than seven days old.

## Outcome

They do not join; the owner can create a fresh invite.
