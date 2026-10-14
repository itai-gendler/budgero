---
domain: explorer
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/explorer-page/ExplorerPage.tsx
- kind: code
  role: implementation
  target: packages/app/src/shared/lib/sql/read-only.ts
---

# Run query

Run a read-only query over the budget's data in the Explorer and chart or
download the result.
