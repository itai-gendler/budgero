---
domain: accounts
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/account-management/ui/EditAccountDialog.tsx
  title: handleDelete
- kind: code
  role: implementation
  target: packages/core/src/services/accounts/index.ts
  title: AccountService.deleteAccount
---

# Delete account

Permanently delete an account that holds no transactions.
