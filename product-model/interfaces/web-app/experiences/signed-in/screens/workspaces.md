---
entities:
- {entity: workspace, shows: [Name], collects: [Name]}
- {entity: workspace-membership, shows: [Role, Joined at]}
- {entity: invitation, shows: [Invitee email, Expires at, Invite link], collects: [Invite link]}
entryPoints:
- web-app: /settings/workspaces
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/WorkspaceSettingsPage.tsx
- kind: code
  role: implementation
  target: packages/app/src/features/budget-sharing/ui/WorkspaceSharingPanel.tsx
---

# Workspaces and sharing

The workspaces the person belongs to, and for the active one its members, pending invitations and the owner's collaborator seats.
