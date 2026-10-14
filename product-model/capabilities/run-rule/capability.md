---
domain: rules
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/rules/index.ts
  title: RulesService.executeRule
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/AutomationRulesPage.tsx
  title: handleExecute
---

# Run rule

Run a rule across the budget's existing transactions now, with Run now or,
after a confirmation, Retro run. Every run is recorded with its changes.
