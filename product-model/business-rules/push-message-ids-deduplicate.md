---
appliesTo:
- {type: capability, id: push-transaction}
- {type: capability, id: update-pushed-transaction}
- {type: capability, id: delete-pushed-transaction}
- {type: entity, id: push-message, facts: [Message id]}
references:
- kind: code
  role: implementation
  target: packages/server/internal/adapter/driving/http/handler/push.go
  title: PushMutation
---

# A message id is accepted once per workspace

A push carrying a message id already queued for the workspace is refused as a duplicate, so retries never add a transaction twice; the id also lets the client update or delete what that push added.
