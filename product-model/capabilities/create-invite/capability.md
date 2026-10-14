---
domain: workspaces-and-sharing
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/server/internal/application/invite.go
  title: CreateInviteUsecase.Execute
- kind: code
  role: implementation
  target: packages/app/src/features/budget-sharing/ui/WorkspaceSharingPanel.tsx
- kind: doc
  role: intent
  target: packages/website/content/docs/sharing.mdx
  title: How sharing works
---

# Create invite

Create a one-time invite link for someone to join the workspace. The secret is
generated on the owner's device; the server stores only its hash and the
workspace key wrapped under it.
