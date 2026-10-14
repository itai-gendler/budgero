---
domain: rules
relations:
- {entity: rule-run, verb: has, cardinality: one-to-many}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/rules/index.ts
- kind: doc
  role: intent
  target: packages/website/content/docs/rules-engine.mdx
  title: Rules Engine
---

# Rule

An automation that matches transactions by payee, memo, amount or account and
applies actions to them: set category, payee, memo or account, remove a memo
pattern, or set or adjust the amount.

## Information kept

- **Name** — the rule name
- **Mode** — Continuous (runs on every new transaction), One time (runs once retroactively) or Autofill (suggests values in the add-transaction form)
- **Conditions** — payee, memo, amount and account conditions joined by AND and OR, where AND binds first
- **Actions** — the actions applied in order, each seeing the result of the previous
- **Run order** — its position when several rules match; ties go to the older rule
- **Enabled** — whether the rule runs or suggests at all
- **Consumed** — for a One time rule, whether it has already run
- **Last run at** — when it last ran
