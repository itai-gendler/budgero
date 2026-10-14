---
appliesTo:
- {type: entity, id: workspace, effect: creates}
permits:
- {actors: [user], when: [{entity: user, fact: Workspace access, is: Granted}]}
references:
- kind: code
  role: implementation
  target: packages/server/internal/application/entitlement_service.go
  title: EntitlementService.HasWorkspaceAccess
---

# Only a person with workspace access creates a workspace

Creating a workspace needs workspace access: always granted on a self-hosted instance, and on Budgero Cloud an active subscription, trial, founding membership or beta access.
