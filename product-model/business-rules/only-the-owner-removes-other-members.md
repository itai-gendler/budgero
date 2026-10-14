---
appliesTo:
- {type: entity, id: workspace-membership, effect: removes}
permits:
- {related: [{verb: has, entity: workspace}, {verb: has, entity: workspace-membership}, {verb: holds, entity: user}], when: [{entity: workspace-membership, fact: Role, is: Owner}, {fact: Role, is: Member}]}
- {related: [{verb: holds, entity: user}], when: [{fact: Role, is: Member}]}
references:
- kind: code
  role: implementation
  target: packages/server/internal/application/space_service.go
  title: SpaceService.RemoveMember
---

# Only the workspace owner removes other members

The owner removes members but never their own owner membership; a member's
membership otherwise ends only by that member's own action, such as a master
password reset.
