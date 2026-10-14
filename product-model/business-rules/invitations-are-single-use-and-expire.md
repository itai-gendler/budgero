---
appliesTo:
- {type: capability, id: redeem-invite}
- {type: entity, id: invitation, facts: [Expires at]}
references:
- kind: code
  role: implementation
  target: packages/server/internal/domain/space.go
  title: SpaceInvite.CanBeRedeemed
---

# An invitation is redeemed once, before it expires

An invitation works once and only until it expires, seven days after creation by default; an expired one is marked expired when someone tries it.
