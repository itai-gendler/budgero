---
appliesTo:
- {type: capability, id: add-transaction}
- {type: capability, id: add-transfer}
- {type: capability, id: mark-occurrence-ready}
references:
- kind: code
  role: implementation
  target: packages/app/src/shared/runtime/app-runtime.ts
  title: applyContinuousRulesIfNeeded
- kind: doc
  role: context
  target: packages/website/content/docs/rules-engine.mdx
  title: Rules engine
---

# Continuous rules run on every newly recorded transaction

After a transaction is added, a transfer is recorded or a recurring
occurrence is posted, every enabled continuous rule of the budget runs on the
new transaction in rule order.
