---
appliesTo:
- {type: capability, id: create-invite}
- {type: capability, id: redeem-invite}
- {type: entity, id: invitation}
references:
- kind: code
  role: implementation
  target: packages/server/internal/application/space_service.go
  title: SpaceService.ensureCollaboratorSlotAvailable
- kind: code
  role: implementation
  target: packages/server/internal/domain/access.go
---

# An owner has at most five collaborator seats

Across all workspaces one person owns, members and pending invitations
together occupy at most five collaborator seats, on Budgero Cloud and
self-hosted instances alike; creating or redeeming an invitation beyond that is
refused.
