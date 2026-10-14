---
domain: accounts
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/account-management/ui/ReconcileAccountDialog.tsx
- kind: code
  role: implementation
  target: packages/core/src/services/transactions/index.ts
  title: TransactionService.reconcileAccount
---

# Reconcile account

Confirm an account against the bank: enter the balance the bank shows, compare
it with the cleared balance, add an adjustment when they differ, and lock the
cleared transactions as reconciled.
