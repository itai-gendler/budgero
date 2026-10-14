---
domain: budget
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/budget-planning/ui/assign-dropdown/assign-dropdown.utils.ts
  title: prepareResetAvailableAssignments
---

# Reset available to zero

Adjust every category's assignment for the viewed month so that its
Available lands exactly on zero.
