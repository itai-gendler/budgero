---
domain: rules
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/rules/index.ts
  title: RulesService.updateRule
---

# Edit rule

Change a rule's name, mode, conditions, actions or run order.
