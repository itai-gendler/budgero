---
domain: budget
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/budget-planning/ui/assign-dropdown/assign-dropdown.utils.ts
  title: prepareOverspentAssignments
- kind: code
  role: implementation
  target: packages/app/src/features/budget-planning/ui/assign-dropdown/useAssignDropdownState.tsx
  title: handleCoverOverspending
---

# Cover overspending

Top up overspent categories from Ready to Assign in one action from the Assign
menu, largest overspending first, for the month being viewed.
