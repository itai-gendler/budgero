---
appliesTo:
- {type: entity, id: invitation, effect: creates}
permits:
- {related: [{verb: has, entity: workspace}, {verb: has, entity: workspace-membership}, {verb: holds, entity: user}], when: [{entity: workspace-membership, fact: Role, is: Owner}, {entity: user, fact: Workspace access, is: Granted}]}
references:
- kind: code
  role: implementation
  target: packages/server/internal/application/invite.go
  title: CreateInviteUsecase.Execute
---

# Only the workspace owner with workspace access creates invitations

Members cannot invite people; the owner can while they have workspace access.
