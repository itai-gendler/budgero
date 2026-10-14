---
entities:
- {entity: report, shows: [Name, Description, Query, Charts, Favorite], collects: [Name, Description, Query, Charts]}
entryPoints:
- web-app: /reports/explorer
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/explorer-page/ExplorerPage.tsx
---

# Explorer

Writing read-only queries over the budget's data, charting the results and keeping them as saved reports.
