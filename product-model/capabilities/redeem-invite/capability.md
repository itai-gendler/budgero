---
domain: workspaces-and-sharing
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/server/internal/application/space_service.go
  title: SpaceService.RedeemInvite
- kind: code
  role: implementation
  target: packages/app/src/pages/JoinWorkspacePage.tsx
---

# Redeem invite

Join a workspace with an invite link or code and the master password, so the
shared key is re-wrapped under the joiner's own master password on their
device.
