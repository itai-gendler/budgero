---
appliesTo:
- {type: entity, id: invitation, effect: removes}
permits:
- {related: [{verb: has, entity: workspace}, {verb: has, entity: workspace-membership}, {verb: holds, entity: user}], when: [{entity: workspace-membership, fact: Role, is: Owner}]}
references:
- kind: code
  role: implementation
  target: packages/server/internal/application/invite.go
  title: DeleteInviteUsecase.Execute
---

# Only the workspace owner cancels invitations

Members cannot revoke an invitation.
