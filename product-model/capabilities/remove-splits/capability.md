---
domain: accounts
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/transactions/split-service.ts
  title: SplitService.clearSplits
---

# Remove splits

Turn a split transaction back into a single entry.
