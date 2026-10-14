---
domain: payees
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/transactions/payee-service.ts
  title: PayeeService.deletePayees
---

# Delete payee

Delete one or more payees and clear them from transactions.
