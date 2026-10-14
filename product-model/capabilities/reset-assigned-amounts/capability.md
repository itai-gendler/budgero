---
domain: budget
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/budget-planning/ui/assign-dropdown/assign-dropdown.utils.ts
  title: prepareResetAssignedAssignments
---

# Reset assigned amounts

Set every category's assignment for the viewed month back to zero to start the
month's plan over.
