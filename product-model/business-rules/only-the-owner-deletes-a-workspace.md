---
appliesTo:
- {type: entity, id: workspace, effect: removes}
permits:
- {related: [{verb: has, entity: workspace-membership}, {verb: holds, entity: user}], when: [{entity: workspace-membership, fact: Role, is: Owner}]}
references:
- kind: code
  role: implementation
  target: packages/server/internal/application/space_service.go
  title: SpaceService.Delete
---

# Only the workspace owner deletes a workspace

A member can never delete a workspace shared with them.
