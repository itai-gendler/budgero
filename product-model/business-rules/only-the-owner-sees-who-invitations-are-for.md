---
appliesTo:
- {type: entity, id: invitation, effect: reads, facts: [Invitee email]}
permits:
- {related: [{verb: has, entity: workspace}, {verb: has, entity: workspace-membership}, {verb: holds, entity: user}], when: [{entity: workspace-membership, fact: Role, is: Owner}]}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/budget-sharing/api/useBudgetSpaceSharing.ts
---

# Only the workspace owner sees who invitations are for

The pending invitations of a workspace, and the address each is meant for, are shown to its owner only.
