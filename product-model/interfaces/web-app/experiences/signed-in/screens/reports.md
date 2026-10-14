---
entities:
- {entity: transaction, shows: [Date, Inflow, Outflow, Category]}
- {entity: account, shows: [Name]}
- {entity: scenario, shows: [Name, Forecast model, Income change, Spending change, Horizon, One-off events], collects: [Name, Forecast model, Income change, Spending change, Horizon, One-off events]}
entryPoints:
- web-app: /reports/prebuilt
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/analytics/AnalyticsPage.tsx
---

# Reports

The prebuilt reports — spending, flow, in and out, plan versus reality, wealth and the scenario planner — over a chosen date range and accounts.
