---
appliesTo:
- {type: capability, id: delete-category}
- {type: entity, id: transaction, facts: [Category]}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/category-management/api/useReassignAndDeleteCategory.ts
---

# A category with history is deleted only after its data moves

Deleting a category that has transactions first moves all of its
transactions and assignments to another category the person chooses; an income
category's history moves only to another income category.
