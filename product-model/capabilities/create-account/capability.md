---
domain: accounts
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/accounts/index.ts
  title: AccountService.createAccount
- kind: code
  role: implementation
  target: packages/app/src/features/account-management/ui/AddAccountDialog.tsx
- kind: doc
  role: intent
  target: packages/website/content/docs/accounts.mdx
  title: Accounts
- kind: doc
  role: intent
  target: packages/website/content/docs/debt-tracking.mdx
  title: Debt Tracking
---

# Create account

Add an account with a name, type, currency and starting balance. On-budget is
preset by type and may be changed only for the types that allow both. A
starting balance is recorded as an opening transaction; credit cards get a
payment category and loans and mortgages a linked category.
