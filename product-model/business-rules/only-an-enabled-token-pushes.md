---
appliesTo:
- {type: capability, id: push-transaction}
- {type: capability, id: update-pushed-transaction}
- {type: capability, id: delete-pushed-transaction}
- {type: capability, id: push-transfer}
- {type: capability, id: delete-pushed-transfer}
- {type: entity, id: push-token, facts: [Enabled]}
references:
- kind: code
  role: implementation
  target: packages/server/internal/application/push_service.go
---

# Only an enabled Push API token is accepted

A push with an unknown, revoked or disabled token is refused and nothing is queued; pushes go into the token owner's default workspace.
