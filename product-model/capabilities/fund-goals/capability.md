---
domain: budget
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/budget-planning/ui/assign-dropdown/useAssignDropdownState.tsx
  title: handleAutoAssignUnderfunded
- kind: code
  role: implementation
  target: packages/app/src/features/budget-planning/ui/assign-dropdown/assign-dropdown.utils.ts
  title: prepareUnderfundedAssignments
- kind: code
  role: implementation
  target: packages/core/src/services/goals/funding.ts
  title: allocateGoalFunding
- kind: doc
  role: intent
  target: packages/website/content/docs/goals.mdx
  title: Goals
---

# Fund goals

Fund every underfunded goal for the viewed month in one action from the Assign
menu, or only the categories selected in the budgeting side panel. Money goes
to the lowest funding priority number first; each funding action is saved as
one batch that undoes in one step.
