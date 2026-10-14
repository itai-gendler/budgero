---
domain: prebuilt-reports
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/analytics/AnalyticsPage.tsx
- kind: code
  role: implementation
  target: packages/core/src/services/recurring/index.ts
  title: RecurringTransactionService.listProjectedTransactions
- kind: doc
  role: intent
  target: packages/website/content/docs/recurring-transactions.mdx
  title: In reports
---

# Browse reports

Read the prebuilt reports — spending, flow, in and out, plan versus reality,
wealth and expenses — over a chosen date range and accounts. A range reaching
past today includes recurring occurrences not yet posted as projections.
