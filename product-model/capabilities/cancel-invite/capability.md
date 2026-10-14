---
domain: workspaces-and-sharing
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/server/internal/application/invite.go
  title: DeleteInviteUsecase.Execute
---

# Cancel invite

Revoke a pending invitation before it is used.
