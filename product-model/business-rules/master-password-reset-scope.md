---
appliesTo:
- {type: capability, id: reset-master-password}
- {type: entity, id: workspace}
references:
- kind: code
  role: implementation
  target: packages/server/internal/application/user_service.go
  title: UserService.ResetData
---

# A master password reset deletes every workspace the person owns

Resetting a forgotten master password permanently deletes each workspace the
person owns, for all of its members, and removes the person from workspaces
shared with them.
