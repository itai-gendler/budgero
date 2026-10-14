---
domain: budget
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/budget-planning/ui/assign-dropdown/assign-dropdown.utils.ts
  title: calculateOverfundedCategories
---

# Reduce overfunding

Pull goal categories that are funded past their target back toward it in one
action from the Assign menu, returning the excess to Ready to Assign.
