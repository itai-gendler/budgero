---
appliesTo:
- {type: entity, id: workspace, effect: changes, facts: [Name]}
permits:
- {related: [{verb: has, entity: workspace-membership}, {verb: holds, entity: user}], when: [{entity: workspace-membership, fact: Role, is: Owner}]}
references:
- kind: code
  role: implementation
  target: packages/server/internal/application/space_service.go
  title: SpaceService.UpdateDisplayName
---

# Only the workspace owner renames a workspace

A member cannot rename a workspace they do not own.
