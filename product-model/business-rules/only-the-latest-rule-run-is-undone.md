---
appliesTo:
- {type: capability, id: undo-rule-run}
- {type: entity, id: rule-run}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/rules/index.ts
  title: RulesService.undoRun
---

# Only a rule's most recent completed run can be undone

Undoing restores every transaction the run changed and lets a One time rule run again; earlier runs cannot be undone.
