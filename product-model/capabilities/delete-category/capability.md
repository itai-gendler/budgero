---
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/budget-planning/ui/BudgetTable.tsx
  title: handleDeleteCategory
- kind: code
  role: implementation
  target: packages/app/src/features/category-management/api/useReassignAndDeleteCategory.ts
- kind: code
  role: implementation
  target: packages/core/src/services/categories/index.ts
  title: CategoryService.deleteCategory
---

# Delete category

Delete a category. A category that has transactions is deleted by first moving
all of its transactions and assignments to another category the person
chooses.
