---
domain: workspaces-and-sharing
references:
- kind: code
  role: implementation
  target: packages/server/internal/domain/space.go
- kind: code
  role: implementation
  target: packages/app/src/features/budget-sharing/ui/WorkspaceSharingPanel.tsx
---

# Membership

A person's place in one workspace. The creator of a workspace holds its Owner
membership; everyone who redeems an invitation holds a Member membership.

## Information kept

- **Role** — Owner or Member
- **Joined at** — when the person joined the workspace
