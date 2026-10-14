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
- text: The invitation has already been redeemed
  kind: condition
  entities:
  - {entity: invitation, effect: reads, facts: [Invite link]}
  contexts:
    web:
      place: web-app::signed-in::join-workspace
- text: The Product refuses the code
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::join-workspace
---

# Refuse an invitation that was already used

## Trigger

A second person opens the same link.

## Outcome

They do not join.

## Edge cases

- A redemption is also refused when the owner has no free collaborator seat left.
