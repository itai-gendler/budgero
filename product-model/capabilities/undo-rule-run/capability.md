---
domain: rules
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/rules/index.ts
  title: RulesService.undoRun
- kind: code
  role: implementation
  target: packages/app/src/features/rules/ui/RuleHistoryDrawer.tsx
---

# Undo rule run

Revert the most recent completed run of a rule from its history.
