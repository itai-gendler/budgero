---
domain: budget
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/categories/index.ts
  title: CategoryService.updateFundingPriorities
- kind: doc
  role: intent
  target: packages/website/content/docs/goals.mdx
  title: Category funding priorities
---

# Change funding priority

Set the funding priority of one category from its row menu, or of several
selected categories at once from the budgeting side panel.
