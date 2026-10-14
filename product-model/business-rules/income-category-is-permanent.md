---
appliesTo:
- {type: capability, id: delete-category}
- {type: capability, id: edit-category}
- {type: capability, id: rename-category-group}
- {type: capability, id: delete-category-group}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/categories/index.ts
  title: CategoryService.deleteCategory
---

# The Income category and group are never renamed or deleted

The system Income category and the Income group cannot be edited or deleted, so income always has a place to land; other income categories may be added beside it.
