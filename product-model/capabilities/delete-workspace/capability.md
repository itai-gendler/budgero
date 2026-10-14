---
domain: workspaces-and-sharing
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/server/internal/application/space_service.go
  title: SpaceService.Delete
---

# Delete workspace

Permanently delete a workspace with its budgets, members and invitations.
