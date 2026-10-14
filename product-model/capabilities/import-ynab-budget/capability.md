---
domain: budgets
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/import/ynab-import-service.ts
- kind: code
  role: implementation
  target: packages/app/src/features/budget-management/ui/create-budget-form/YnabImportTab.tsx
- kind: doc
  role: intent
  target: packages/website/content/docs/ynab-import.mdx
  title: YNAB Import
---

# Import YNAB budget

Create a budget from YNAB, either by connecting directly with a YNAB personal
access token or from a YNAB export ZIP, and check the result against YNAB
before keeping it.
