---
appliesTo:
- {type: capability, id: delete-category-group}
- {type: entity, id: category-group}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/budget-planning/ui/budget-table/useCategoryOperations.ts
  title: handleDeleteCategoryGroup
---

# Only empty category groups are deleted

A category group is deleted only when it holds no category, so no category is ever orphaned.
