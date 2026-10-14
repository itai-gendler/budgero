---
domain: payees
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/transactions/payee-service.ts
  title: PayeeService.renamePayee
---

# Rename payee

Rename a payee everywhere it is used.
