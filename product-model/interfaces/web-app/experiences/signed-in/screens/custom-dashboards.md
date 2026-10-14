---
entities:
- {entity: dashboard, shows: [Name], collects: [Name]}
- {entity: widget, shows: [Chart, Title], collects: [Title]}
- {entity: report, shows: [Name, Charts]}
entryPoints:
- web-app: /reports/dashboards
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/custom-dashboards/CustomDashboardsPage.tsx
---

# Custom dashboards

The budget's dashboards and the charts pinned to them.
