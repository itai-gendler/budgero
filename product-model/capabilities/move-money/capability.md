---
domain: budget
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/budget-planning/ui/budget-table/useCategoryOperations.ts
  title: handleMoveMoney
- kind: code
  role: implementation
  target: packages/app/src/features/budget-planning/ui/category-row/MoveMoneyPopover.tsx
---

# Move money

Move money out of one category's Available into another category, or back
to Ready to Assign, in the month being viewed, keeping the trade-off explicit.
