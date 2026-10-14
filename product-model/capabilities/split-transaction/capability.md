---
domain: accounts
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/transactions/split-service.ts
  title: SplitService.upsertSplits
---

# Split transaction

Split one transaction into lines, each with its own amount, memo and payee
and either a category or a transfer account, adding up exactly to the
transaction's total.
