---
domain: rules
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/rules/index.ts
  title: RulesService.createRule
- kind: code
  role: implementation
  target: packages/app/src/features/rules/ui/rule-editor/RuleEditorDialog.tsx
---

# Create rule

Create a rule with a name, mode, conditions, ordered actions and run order.
