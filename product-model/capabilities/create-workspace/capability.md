---
domain: workspaces-and-sharing
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/server/internal/application/invite.go
  title: CreateSpaceUsecase.Execute
- kind: code
  role: implementation
  target: packages/server/internal/application/space_service.go
  title: SpaceService.Create
---

# Create workspace

Create a new workspace, owned by its creator, and switch to it.
