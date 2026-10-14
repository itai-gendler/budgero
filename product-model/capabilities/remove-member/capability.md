---
domain: workspaces-and-sharing
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/server/internal/application/space_service.go
  title: SpaceService.RemoveMember
- kind: code
  role: implementation
  target: packages/server/internal/adapter/driving/http/handler/budget_spaces.go
  title: RemoveBudgetSpaceMember
---

# Remove member

Remove a member from a workspace, ending their access to new data.
