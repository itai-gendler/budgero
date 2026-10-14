---
appliesTo:
- {type: capability, id: assign-money}
- {type: capability, id: fund-goals}
- {type: capability, id: cover-overspending}
- {type: entity, id: workspace, facts: [Allow over-assignment]}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/budget-planning/ui/budget-table/useCategoryOperations.ts
  title: handleUpsertAssignment
- kind: code
  role: implementation
  target: packages/app/src/features/budget-planning/ui/assign-dropdown/AssignQuickActions.tsx
---

# Assignments never exceed Ready to Assign unless over-assignment is allowed

While the workspace does not allow over-assignment, an assignment increase
larger than Ready to Assign is refused, Fund Goals and Cover Overspending spend
at most positive Ready to Assign, and both are unavailable while Ready to
Assign is zero or negative. With over-assignment allowed, assignments and goal
funding may take Ready to Assign below zero.
