---
domain: accounts
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/accounts/index.ts
  title: AccountService.setAccountArchived
---

# Archive account

Close an account without losing its history.
