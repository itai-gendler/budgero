---
entities:
- {entity: rule, shows: [Name, Mode, Conditions, Actions, Run order, Enabled, Consumed, Last run at], collects: [Name, Mode, Conditions, Actions, Run order]}
- {entity: rule-run, shows: [Trigger, Evaluated, Changed, Changes, Errors]}
entryPoints:
- web-app: /settings/rules
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/AutomationRulesPage.tsx
---

# Rules

Every rule of the budget in run order, with its mode, conditions, actions, last run and run history.
