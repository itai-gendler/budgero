---
appliesTo:
- {type: entity, id: invitation, effect: changes}
permits:
- {actors: [user]}
references:
- kind: code
  role: implementation
  target: packages/server/internal/application/space_service.go
  title: SpaceService.RedeemInvite
---

# Any signed-in person holding the link redeems an invitation

Whoever signs in with the invite link and a master password may redeem it, once; the attempt after expiry marks it expired.
