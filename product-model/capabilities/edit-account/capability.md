---
domain: accounts
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/accounts/index.ts
  title: AccountService.updateAccount
- kind: code
  role: implementation
  target: packages/app/src/features/account-management/ui/EditAccountDialog.tsx
---

# Edit account

Change an account's name, type, currency, on-budget setting or debt details.
