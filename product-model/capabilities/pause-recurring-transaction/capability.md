---
domain: recurring-transactions
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/recurring/index.ts
---

# Pause recurring transaction

Pause a recurring template so it stops reminding.
