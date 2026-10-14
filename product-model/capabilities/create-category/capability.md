---
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/categories/index.ts
  title: CategoryService.addCategory
- kind: doc
  role: intent
  target: packages/website/content/docs/categories.mdx
  title: Categories
---

# Create category

Add a category to a group of the budget table, or an income category to the
Income group from the budget settings. New categories start at funding
priority 3 (Normal).
