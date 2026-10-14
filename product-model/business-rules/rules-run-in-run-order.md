---
appliesTo:
- {type: capability, id: run-rule}
- {type: capability, id: add-transaction}
- {type: entity, id: rule, facts: [Run order, Mode]}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/rules/index.ts
  title: RulesService.executeRule
- kind: doc
  role: intent
  target: packages/website/content/docs/rules-engine.mdx
  title: 'Ordering: when several rules match'
---

# Every matching rule runs, in run order

Rules do not stop at the first match: every enabled matching rule runs, in
ascending run order with ties going to the older rule, and each action sees the
result of the previous one. Continuous rules run on new transactions, One time
rules once, and Autofill rules only suggest values in the add-transaction form,
once per entry.
