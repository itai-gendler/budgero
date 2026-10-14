---
domain: budget
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/categories/index.ts
  title: CategoryService.addCategoryGroup
---

# Create category group

Add a new group to the budget table.
