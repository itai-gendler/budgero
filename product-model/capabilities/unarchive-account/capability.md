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

# Unarchive account

Return an archived account to day-to-day use.
