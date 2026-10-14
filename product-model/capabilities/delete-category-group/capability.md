---
domain: budget
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/budget-planning/ui/budget-table/useCategoryOperations.ts
  title: handleDeleteCategoryGroup
---

# Delete category group

Delete a category group that no longer holds any category.
