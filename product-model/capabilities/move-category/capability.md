---
domain: budget
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/budget-planning/ui/budget-table/useCategoryOperations.ts
  title: handleReorderItems
---

# Move category

Drag a category into another category group. Its transactions, assignments,
goal and history follow it unchanged.
