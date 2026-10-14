---
domain: explorer
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/reports/index.ts
- kind: code
  role: implementation
  target: packages/app/src/pages/explorer-page/hooks/useReportActions.ts
---

# Save report

Save a query with its charts as a named report.
