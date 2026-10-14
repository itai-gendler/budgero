---
domain: prebuilt-reports
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/scenarios/index.ts
  title: ScenarioService
- kind: code
  role: implementation
  target: packages/app/src/pages/analytics/reports/ScenarioReport.tsx
---

# Save scenario

Save the scenario planner's assumptions under a name, or update a saved
scenario.
