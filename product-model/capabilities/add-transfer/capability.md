---
domain: accounts
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/shared/mutations/op-code-registry/domains/transactions.ts
  title: '''transactions.addTransfer'''
- kind: code
  role: implementation
  target: packages/core/src/services/monthly-budgets/queries.ts
  title: MonthlyBudgetQueries.readyToAssign
- kind: doc
  role: intent
  target: packages/website/content/docs/debt-tracking.mdx
  title: Debt Tracking
---

# Add transfer

Move money between two of the budget's accounts as a transfer: two linked legs
in the Transfers category, created and deleted together.
